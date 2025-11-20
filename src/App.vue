<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
  <div v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal" />
  </div>
  <div class="handle-modal">
    <button @click.alt="toggleModal">Open modal (alt + click)</button>
    <!-- <button @click.shift="toggleModal">Open modal (shift + click)</button> -->
    <!-- <button @click.right="toggleModal">Open modal (right click)</button> -->
  </div>
</template>
<!--
В компоненте App.vue:
При использовании компонента Modal есть обработчик @close="toggleModal".
Когда в Modal происходит событие close, вызывается метод toggleModal в родительском компоненте.

Родительский компонент App ловит это событие Modal через @close и выполняет метод toggleModal.
toggleModal переключает значение showModal между true и false, что управляет отображением модального окна.

-->
<script>
import Modal from './components/Modal.vue';

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "Это мое первое приложение на Vue.js",
      header: "Sign up for the Giveaway!",
      text: "Grab your ninja swag for half price!",
      showModal: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    }
  }
};
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

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

.handle-modal {
  margin: 10px;
}
</style>
