<template>
  <div class="input">
    <label class="input__label">{{ input.label }}
      <input
          :type=input.type
          class="input__field"
          :name=input.name
          :placeholder=input.placeholder
          v-model.trim="value"
          @input="onInput"
      >
    </label>
    <span
        class="input__error"
        v-if="input.change && !input.valid"
    >{{ input.error }}</span>
  </div>
</template>

<script>
export default {
  name: "Input",
  props: {
    input: Object,
    inputIndex: Number
  },
  data () {
    return {
      value: null
    }
  },
  methods: {
    onInput() {
      this.$emit('inputChange', this.inputIndex, this.value);
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.input {
  position: relative;
  padding-bottom: 33px;
}

.input__label {
  display: flex;
  flex-direction: column;
  color: $text-light;
  font-weight: 500;
}

.input__field {
  padding: 15px 16px;
  margin-top: 7px;
  width: 100%;
  background: $white;
  border: 1px solid $input-border-color;
  box-shadow: 0 4px 8px $input-shadow-color;
  border-radius: 6px;
  font-size: 16px;
  line-height: 21px;
  color: $text-main;
  font-family: "IBM Plex Sans", "Arial", sans-serif;

  &::placeholder {
    color: $text-light-blue;
  }

  &:focus {
    outline: none;
    border: 2px solid $input-border-focus-color;
    padding: 14px 15px;
  }

  &:hover {
    border: 2px solid $input-border-focus-color;
    padding: 14px 15px;
  }
}

.input__error {
  position: absolute;
  bottom: 8px;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
