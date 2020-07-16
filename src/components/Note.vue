<template>
    <div class='note'>
        <h6 class='note__title'>{{ note.title }}</h6>
        <div class="note__details">
            <input class="note__checkbox" type="checkbox" @click="statusChanged(note.id)" :checked="note.done"/>
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
            },

            statusChanged(id) {
                this.$emit('status-changed', id);
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
            width: 350px
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

        &__checkbox 
            position: relative
            width: 40px
            height: 20px
            -webkit-appearance: none
            background-color: $colors--tertiary
            border-radius: 50px
            box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2)
            transition: background-color .5s
            cursor: pointer

            &:checked 
                background-color: $colors--quaternary
            &:before 
                content: ''
                position: absolute
                top: 0
                left: 0
                width: 20px
                height: 20px
                background-color: $colors--secondary
                border-radius: calc(40px / 2)
                transform: scale(1.1)
                box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2)
                transition: .5s
                
            &:checked:before 
                left: 20px

            &:focus
                outline: none
                
    @media only screen and (max-width: 800px) 
        .note 
            width: 150vw

            &__title
                min-width: 80vw
                padding-right: 30px

            &__details
                width: 70vw

  
                

</style>