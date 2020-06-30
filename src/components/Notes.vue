<template>
    <div class='notes'>
        <div :key="note.id" v-for="note in notes">
            <Note v-bind:note="note"/>
        </div>
    </div>
</template>

<script>
    import Note from '@/components/Note';

    export default {
        name: 'Notes',
        props: ['notes'],
        components: {
            Note
        },
    }
</script>

<style lang="sass" scoped>
    .notes
        margin-top: 50px
</style>