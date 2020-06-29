<template>
  <header class="header home">
    <div class="row">
      <div class="">    
        <h1 class='title title--lg'>
          Best app for taking notes and keeping your thoughts in order
        </h1>
        <router-link to="/board" class='btn'>Start for free</router-link>
      </div>
      <div class="">
        <img :src='image' alt="">
      </div>
    </div>
  </header>
</template>

<script>
  import Marcus_Aurelius from '@/assets/Marcus_Aurelius.png'


  export default {
    name: 'Home',
    data: function () {
        return {
            image: Marcus_Aurelius
        }
    }
  }
</script>


<style scoped lang='sass'>
  .home
    align-items: flex-end
    display: flex

  .row
    display: grid
    grid-template-columns: repeat(2, 1fr)
    grid-gap: $margins--md
  
  img
    max-width: 40vw
    position: absolute
    right: -100px
    top: 100px
    opacity: .7

    &:hover
      opacity: 1
      max-width: calc(40vw + 50px)
</style>