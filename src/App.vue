<script setup>
</script>

<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal"> <!-- teleports it to index.html -->
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>

    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModalTwo"> 
    <Modal @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes</p>
    </Modal>
  </teleport>
  
  <button @click.alt="toggleModal">Open modal (alt)</button>
  <button @click="toggleModalTwo">Open modal two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data(){
    return {
      title: "My first Vue App :)",
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
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
#app, .modals{
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

</style>
