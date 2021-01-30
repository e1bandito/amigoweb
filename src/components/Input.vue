<template>
  <div class="input">
    <label class="input__label">Имя
      <input type="text" class="input__field" placeholder="Введите Ваше имя">
    </label>
    <span class="input__error">Введено не корректное значение</span>
  </div>
</template>

<script>
export default {
  name: "Input"
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.input {
  position: relative;
  padding-bottom: 24px;
}

.input__label {
  display: flex;
  flex-direction: column;
  color: $text-light;
  font-weight: 500;
}

.input__field {
  padding: 16px 16px 15px;
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
    padding: 15px 15px 14px;
  }

  &:hover {
    border: 2px solid $input-border-focus-color;
    padding: 15px 15px 14px;
  }
}

.input__error {
  display: none;

  position: absolute;
  bottom: 0;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
