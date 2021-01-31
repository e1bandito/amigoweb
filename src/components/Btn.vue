<template>
  <button class="btn"
          @click="clickBtn"
          :disabled="!formValid"
  >Зарегистрироваться</button>
</template>

<script>
export default {
  name: "Btn",
  props: {
    formValid: Boolean
  },
  methods: {
    clickBtn() {
      this.$emit('click');
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.btn {
  display: inline-block;
  width: 100%;
  font-family: "IBM Plex Sans", "Arial", sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: 21px;
  text-align: center;
  color: $btn-text-color;
  background-color: $btn-bg;
  border: 2px solid $btn-bg;
  border-radius: 6px;
  padding: 16px 16px 15px;
  cursor: pointer;
  box-shadow: $btn-shadow;
  transition: box-shadow 0.3s;

  &:hover {
    box-shadow: $btn-shadow-hover;
  }

  &:active {
    border-color: $btn-border-active;
  }

  &:disabled {
    background-color: $btn-bg-disabled;
    border-color: $btn-bg-disabled;
    color: $text-main;
    cursor: not-allowed;

    &:hover {
      box-shadow: $btn-shadow;
    }
  }
}
</style>
