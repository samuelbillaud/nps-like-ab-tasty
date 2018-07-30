<template>
  <div id="app">
    <Modal :isActive="isActive" @closeModal="isActive = false"/>
  </div>
</template>

<script>
import Modal from './components/Modal'

export default {
  name: 'App',
  data () {
    return {
      isActive: false
    }
  },
  components: {
    Modal
  },
  mounted () {
    console.log('test')
    setTimeout(() => {
      this.isActive = true
    }, 2000)
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
