<template>
  <header class="header about">
    <h1 class='title title--lg'>
      Notes board
    </h1>
    <Form @addNewNote="addNewNote"/>
    <Notes :notes="notes" @note-deleted="deleteNote" @status-changed="statusChanged"/>
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

      statusChanged(id) {
        this.notes.map(note => {
          if(note.id === id){
            note.done = !note.done
          }
          console.log(note.done);
        })
      }
    },
  }


  
        
</script>

<style scoped lang="sass">
  .title
    width: 100%
  
</style>