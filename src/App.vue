<template>
  <div id="app">
    <Form
        :fields="fields"
        @selected="selected"
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
        ],
        selects: [
          {
            id: 'select-1',
            name: 'language',
            options: [
              {
                value: 'russian',
                text: 'Русский',
                active: false
              },
              {
                value: 'English',
                text: 'Английский',
                active: false
              },
              {
                value: 'China',
                text: 'Китайский',
                active: false
              },
              {
                value: 'Spain',
                text: 'Испанский',
                active: false
              }
            ],
            label: 'Язык',
            placeholder: 'Язык',
            error: 'Выберите один из пунктов',
            valid: false,
            change: false
          }
        ]
      }
    }
  },
  methods: {
    selected (itemIndex, selectIndex) {
      const select = this.fields.selects[selectIndex];
      select.options.forEach(el => el.active = false);
      select.placeholder = select.options[itemIndex].text
      select.options[itemIndex].active = true;
      select.change = true;
      select.valid = true;
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
