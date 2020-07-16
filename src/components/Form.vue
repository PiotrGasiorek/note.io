<template>
    <form @submit.prevent='submitForm' v-on:keyup.enter='submitForm'>
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

                this.$emit('addNewNote', { "title": this.note, "time": details[1], "date": details[0], "id": Math.random(), "done": false });
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
    form
        display: flex

    .input
        background: transparent
        border: none
        border-radius: 0px
        border-bottom: 2px solid transparent
        font-family: $font-families--secondary
        font-weight: $font-weights--regular
        font-size: 20px
        padding: 5px 10px

        &:focus
            outline: none
            border-bottom: 2px solid $colors--secondary

    .submit
        width: 42.15px
        height: 42.15px
        border: none
        border-radius: 0px
        color: $colors--primary
        font-size: 30px
        line-height: 0px

        &:focus
            outline: none

    .error
        border-bottom-color: #B71010

    @media only screen and (max-width: 480px) 
        .input
            width: calc(100% - 42.15px) !important

</style>