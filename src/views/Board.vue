<template>
  <header class="header about">
    <h1 class='title title--lg'>
      Notes board
    </h1>
    <Form @addNewNote="addNewNote"/>
    <Notes :notes="notes" @note-deleted="deleteNote"/>
  </header>
</template>

<script>
  import Form from '@/components/Form';
  import Notes from '@/components/Notes';

  export default {
    name: 'Board',
    data() {
        return {
          notes: [],
        }
    },
    components: {
      Form,
      Notes
    },
    methods: {
      addNewNote(note) {
        this.notes.unshift(note);
      },
      deleteNote(id) {
        this.notes = this.notes.filter(note => {
          return note.id !== id;
        })
      },
    },
  }


  
        
</script>

<style scoped lang="sass">
  .title
    width: 100%
  
</style>