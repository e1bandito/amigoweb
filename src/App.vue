<template>
  <div id="app">
    <Form/>
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  }
}
</script>

<style lang="scss">
@import "assets/styles/helpers";

#app {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}
</style>
