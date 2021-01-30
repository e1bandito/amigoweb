<template>
  <div class="checkbox">
    <input id="checkbox" type="checkbox" class="checkbox__field visually-hidden" placeholder="Введите Ваше имя">
    <label for="checkbox" class="checkbox__label">Принимаю <a href="#" class="checkbox__link">условия</a> использования</label>
    <span class="checkbox__error">Примите условия использования</span>
  </div>
</template>

<script>
export default {
  name: "Checkbox"
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";
@import "src/assets/styles/helpers";

.checkbox {
  position: relative;
  padding-bottom: 24px;
}

.checkbox__label {
  position: relative;
  padding-left: 36px;
  color: $text-light;
  font-weight: 500;
  cursor: pointer;
  user-select: none;

  &::before {
    content: "";
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    margin: auto;
    width: 28px;
    height: 28px;
    background-color: $white;
    border: 1px solid $checkbox-border-color;
    box-shadow: 0 4px 8px $checkbox-shadow-color;
    border-radius: 4px;
  }

  &::after {
    position: absolute;
    top: 4px;
    left: 8px;
    margin: auto;
    border-left: 1px solid $checkbox-border-check-color;
    border-bottom: 1px solid $checkbox-border-check-color;
    width: 13px;
    height: 7px;
    transform: rotate(-45deg);
  }
}

.checkbox__field:checked + .checkbox__label::before {
  border: 2px solid $checkbox-border-check-color;
}

.checkbox__field:checked + .checkbox__label::after {
  content: "";
}

.checkbox__field:focus + .checkbox__label::before {
  border: 2px solid $checkbox-border-check-color;
}

.checkbox__link {
  color: $text-blue;

  &:hover {
    color: $text-light-blue;
  }
}

.checkbox__error {
  display: none;

  position: absolute;
  bottom: 0;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
