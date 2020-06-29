<template>
    <div class='note'>
        <h6 class='note__title'>{{ note.title }}</h6>
        <div class="note__details">
            <p className='note__time'>{{ note.time }}</p>
            <p className='note__date'>{{ note.date }}</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Note',
        props: ['note']
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
            width: 200px
            margin-left: auto
            color: $colors--tertiary
            font-size: 16px

            *
                width: 50%

        &__date
            text-align: right
            margin-left: auto

</style>