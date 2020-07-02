<template>
    <div class='note'>
        <h6 class='note__title'>{{ note.title }}</h6>
        <div class="note__details">
            <img :src="delete_icon" alt="Delete icon" @click="deleteNote(note.id)">
            <p className='note__time'>{{ note.time }}</p>
            <p className='note__date'>{{ note.date }}</p>
        </div>
    </div>
</template>

<script>
    import delete_icon from '@/assets/icons/delete.svg';

    export default {
        name: 'Note',
        props: ['note'],
        data: function () {
            return {
                delete_icon: delete_icon
            }
        },
        methods: {
            deleteNote(id) {
                this.$emit('note-deleted', id);
            }
        },
    }
</script>

<style scoped lang='sass'>
    .note
        width: 100%
        display: flex
        height: 60px
        align-items: center
        font-family: $font-families--secondary
        font-weight: $font-weights--regular

        &__title
            font-size: 18px
        &__details
            display: flex
            align-items: center
            width: 300px
            margin-left: auto
            color: $colors--tertiary
            font-size: 16px
            justify-content: space-between

            img 
                width: 25px

                &:hover
                    cursor: pointer
                    

        &__date
            text-align: right

</style>