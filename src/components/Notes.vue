<template>
    <div class='notes'>
        <div :key="note.id" v-for="note in notes">
            <Note v-bind:note="note" @note-deleted="deleteNote"/>
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
        methods: {
            deleteNote(id) {
                this.$emit('note-deleted', id);
            }
        },
    }
</script>

<style lang="sass" scoped>
    .notes
        margin-top: 50px
</style>