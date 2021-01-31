<template>
  <div class="form">
    <form
        action=""
        class="form__body"
        @submit.prevent="onClick"
    >
      <h1
          class="form__title"
          :class="{'form__title--disabled': !formValid}"
      >Регистрация</h1>
      <p class="form__text">Уже есть аккаунт? <a href="#" class="form__link">Войти</a></p>
      <Input
          v-for="(input, index) in fields.inputs"
          :key=fields.inputs[index].id
          :input="input"
          :inputIndex="index"
          @inputChange="inputChange"
      />
      <Select
          v-for="(select, index) in fields.selects"
          :key=fields.selects[index].id
          :selectIndex="index"
          :select="select"
          @change="change"
          @selected="selected"
      />
      <Checkbox
          v-for="(checkbox, index) in fields.checkboxes"
          :key=fields.checkboxes[index].id
          :checkbox="checkbox"
          :checkboxIndex="index"
          @change="checked"
      />
      <Btn
      @click="onClick"
      :form-valid="formValid"
      />
    </form>
  </div>
</template>

<script>
import Select from "@/components/Select";
import Input from "@/components/Input";
import Checkbox from "@/components/Checkbox";
import Btn from "@/components/Btn";

export default {
  name: 'Form',
  components: {
    Btn,
    Checkbox,
    Select,
    Input
  },
  props: {
    fields: Object,
    formValid: Boolean
  },
  methods: {
    onClick () {
      console.log(1);
    },
    selected (itemIndex, selectIndex) {
      this.$emit('selected', itemIndex, selectIndex);
    },
    change (selectIndex) {
      this.$emit('change', selectIndex);
    },
    checked (checked, checkboxIndex) {
      this.$emit('checked', checked, checkboxIndex);
    },
    inputChange (index, value) {
      this.$emit('inputChange', index, value);
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.form {
  width: 100%;
  max-width: 460px;
  padding: 40px 30px;
  background-color: $white;
  border-radius: 24px;
  box-shadow: $form-shadow;
}

.form__title {
  font-size: 34px;
  line-height: 44px;
  margin: 0 0 8px 0;
  color: $text-main;

  &--disabled {
    color: $text-lighter;
  }
}

.form__text {
  margin: 0 0 56px 0;
  font-size: 16px;
  line-height: 22px;
}

.form__link {
  font-size: 16px;
  line-height: 22px;
  color: $text-blue;
  transition: color 0.3s;

  &:hover {
    color: $text-light-blue;
  }
}
</style>
