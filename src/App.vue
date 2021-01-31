<template>
  <div id="app">
    <Form
    :fields="fields"
    />
  </div>
</template>

<script>
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    Form
  },
  data () {
    return {
      fields: {
        inputs: [
          {
            id: 'input-1',
            name: 'name',
            type: 'text',
            label: 'Имя',
            placeholder: 'Введите Ваше имя',
            pattern: null,
            error: 'Введено не корректное значение',
            valid: false,
            change: false
          },
          {
            id: 'input-2',
            name: 'email',
            type: 'email',
            label: 'Email',
            placeholder: 'Введите ваш email',
            pattern: null,
            error: 'Введено не корректное значение',
            valid: false,
            change: false
          },
          {
            id: 'input-3',
            name: 'phone',
            type: 'tel',
            label: 'Номер телефона',
            placeholder: 'Введите номер телефона',
            pattern: null,
            error: 'Введено не корректное значение',
            valid: false,
            change: false
          }
        ],
        checkboxes: [
          {
            id: 'checkbox-1',
            name: 'policy',
            type: 'checkbox',
            label: 'Принимаю  <a href="#" class="checkbox__link">условия</a>  использования',
            error: 'Примите условия использования',
            valid: false,
            change: false
          }
        ]
      }
    }
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
