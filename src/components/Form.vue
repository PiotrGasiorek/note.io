<template>
    <form @submit.prevent='submitForm'>
        <input v-bind:class="[errorExist ? 'error' : '', 'input']" type="text" placeholder="Type here..." v-model='note'>
        <button class="submit" type='submit'>+</button>
    </form>
</template>

<script>

    export default {
        name: 'Form',
        data() {
            return {
                note: '',
                errorExist: false
            }
        },

        methods: {
            submitForm() {
                console.log('Form submited');
                this.validateForm();
            },

            validateForm() {
                this.note === '' ? this.underlineError() : this.addNewNote();
            },

            addNewNote() {
                this.errorExist = false
                const details = this.getDetails();

                this.$emit('addNewNote', { "title": this.note, "time": details[1], "date": details[0], "id": Math.random() });
                this.clearForm();
            },

            clearForm() {
                document.querySelector('.input').value = '';
                this.note = '';
            },

            underlineError(){
                this.errorExist = true
            },

            getDetails() {
                const currentDate = new Date();
                let addZero = (num) => {
                    return num < 10 ? '0' + num : num;
                }

                const date = `${addZero(currentDate.getDate())}.${addZero(currentDate.getMonth() + 1)}.${currentDate.getFullYear()}`;
                const time = `${addZero(currentDate.getHours())}:${addZero(currentDate.getMinutes())}`;

                return [date, time]
            }
        }
    }
</script>

<style scoped lang="sass">
    .error
        border-bottom-color: #B71010
</style>