<template>
  <div id="app">
    <Form
        :fields="fields"
        @selected="selected"
        @checked="checked"
        @change="change"
        @inputChange="inputChange"
        :formValid="formValid"
        @submitForm="getUserInfo"
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
  data() {
    return {
      userData: {
        name: null,
        email: null,
        phone: null,
        lang: null,
        policy: false
      },
      fields: {
        inputs: [
          {
            id: 'input-1',
            name: 'name',
            value: null,
            type: 'text',
            label: 'Имя',
            placeholder: 'Введите Ваше имя',
            pattern: /^[а-яА-Яa-zA-Z(\s-)]+$/i,
            error: 'Введено не корректное значение',
            valid: false,
            change: false
          },
          {
            id: 'input-2',
            name: 'email',
            value: null,
            type: 'email',
            label: 'Email',
            placeholder: 'Введите ваш email',
            pattern: /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/,
            error: 'Введено не корректное значение',
            valid: false,
            change: false
          },
          {
            id: 'input-3',
            name: 'phone',
            value: null,
            type: 'tel',
            label: 'Номер телефона',
            placeholder: 'Введите номер телефона',
            pattern: /^\+?[0-9][-\(]?\d{3}\)?-?\d{3}-?\d{2}-?\d{2}$/, // eslint-disable-line
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
                value: 'Russian',
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
            value: null,
            error: 'Выберите один из пунктов',
            valid: false,
            change: false
          }
        ]
      }
    }
  },
  methods: {
    selected(itemIndex, selectIndex) {
      const select = this.fields.selects[selectIndex];
      select.options.forEach(el => el.active = false);
      select.placeholder = select.options[itemIndex].text
      select.options[itemIndex].active = true;
      select.value = select.options[itemIndex].value;
      select.change = true;
      select.valid = true;
    },
    change(selectIndex) {
      const select = this.fields.selects[selectIndex];
      select.change = true;
    },
    checked(checked, checkboxIndex) {
      const checkbox = this.fields.checkboxes[checkboxIndex];
      checkbox.change = true;
      checkbox.valid = checked;
    },
    inputChange(index, value) {
      const input = this.fields.inputs[index];
      input.change = true;
      input.value = value;
      input.valid = input.pattern.test(value);
    },
    getUserInfo() {
      this.userData.name = this.fields.inputs[0].value;
      this.userData.email = this.fields.inputs[1].value;
      this.userData.phone = this.fields.inputs[2].value;
      this.userData.policy = this.fields.checkboxes[0].valid;
      this.userData.lang = this.fields.selects[0].value;
      console.log(this.userData);
    }
  },
  computed: {
    formValid: function() {
      const inputArr = this.fields.inputs;
      const selectArr = this.fields.selects;
      const checkboxArr = this.fields.checkboxes;
      return (inputArr.every(el => el.valid === true) && selectArr.every(el => el.valid === true) && checkboxArr.every(el => el.valid === true));
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
