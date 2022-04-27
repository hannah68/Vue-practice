<template>
  <h1>my app</h1>
  <p>Welcome...</p>
  <!-- if we want that some part of our code goes for example inside .modal below app we use teleport -->
  <teleport to=".modals" v-if="showModal">
    <!-- close is a custom event -->
    <Modal :header="header" :text="text" :theme="sale" @close="toggleModal">
      <!-- name slot-->
      <template v-slot:links>
        <a href="#">sign up</a>
        <a href="#">more info</a>
      </template>
      <!-- we use slots for passing custom template -->
      <p>this is template</p>
    </Modal>
    
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <p>this is a second modal</p>
    </Modal>
  </teleport>
  
  <!-- .alt is a modifier -->
  <button @click.alt="toggleModal">Open modal(alt)</button>
  <button @click="toggleModalTwo">Open modal2</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components:{Modal},
  data(){
    return {
      title: 'Modal',
      header: 'This is Modal header',
      text: 'This is text modal',
      showModal:false,
      showModalTwo:false
    }
  },
  methods: {
    toggleModal(){
      this.showModal = !this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
