<template>
  <header class="header about">
    <h1 class='title title--lg'>
      Notes board
    </h1>
    <Form @addNewNote="addNewNote"/>
    <Notes :notes="notes"/>
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
        this.postData(note);
      },
      getData() {
        const url = "https://my-json-server.typicode.com/PiotrGasiorek/note.io.api/notes";
        let options = {
          method: "GET",
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          }
        };

        fetch(url, options)
          .then(data => data.json())
          .then(data => {
            data.forEach(note => {
              this.notes.unshift(note)
            });
            console.log(this.notes);
          })
          .catch(err => console.log(err))
      },
      postData(note) {
        const url = "https://my-json-server.typicode.com/PiotrGasiorek/note.io.api/notes";
        let options = {
          method: 'POST',
          body: JSON.stringify(note),
          headers: {
            "Content-type": "application/json; charset=UTF-8"
          }
        };

        fetch(url, options)
          .then(data => data.json())
          .then(data => console.log(data.title))
          .catch(err => console.log(err))
        
        this.notes.unshift(note);
        this.getData();
      },
      
    }, 
    beforeMount() {
      this.getData();
    },
  }


  
        
</script>

<style scoped lang="sass">
  .title
    width: 100%
  
</style>