<template>
    <div class='notes'>
        <div :key="note.id" v-for="note in notes">
            <Note v-bind:note="note" @note-deleted="deleteNote" @status-changed="statusChanged"/>
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
            },

            statusChanged(id) {
                this.$emit('status-changed', id);
            }
        },
    }
</script>

<style lang="sass" scoped>
    .notes
        margin-top: 50px
        overflow: auto
</style>