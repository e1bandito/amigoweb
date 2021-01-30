<template>
  <div class="select">
    <p class="select__label">Язык</p>
    <div class="select__inner">
      <div class="select__placeholder">Язык</div>
      <ul class="select__list">
        <li class="select__item">Русский</li>
        <li class="select__item">Английский</li>
        <li class="select__item">Китайский</li>
        <li class="select__item">Испанский</li>
      </ul>
    </div>
    <span class="select__error">Выберите один из пунктов</span>
  </div>
</template>

<script>
export default {
  name: "Select"
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.select {
  position: relative;
  width: 100%;
  padding-bottom: 20px;
}

.select__label {
  margin: 0 0 7px 0;
  color: $text-light;
}

.select__inner {
  position: relative;
  margin-bottom: 8px;
}

.select__placeholder {
  position: relative;
  width: 100%;
  background-color: $white;
  border: 1px solid $input-border-color;
  box-sizing: border-box;
  box-shadow: 0 4px 8px $input-shadow-color;
  border-radius: 6px;
  cursor: pointer;
  padding: 15px 57px 14px 16px;
  color: $text-light-blue;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;

  &::after {
    content: "";
    position: absolute;
    top: 14px;
    right: 20px;
    width: 16px;
    height: 16px;
    border-left: 2px solid $input-border-focus-color;
    border-bottom: 2px solid $input-border-focus-color;
    transform: rotate(-45deg);
  }

  &:hover {
    border: 2px solid $input-border-focus-color;
    padding: 14px 56px 13px 15px;
    color: $text-main;

    &::after {
      top: 13px;
      right: 19px;
    }
  }
}

.select__list {
  display: none;

  list-style: none;
  margin: 0;
  position: absolute;
  width: 100%;
  top: calc(100% + 4px);
  left: 0;
  background: $white;
  border: 1px solid $select-body-border;
  box-sizing: border-box;
  box-shadow: $select-body-shadow;
  border-radius: 6px;
  padding: 12px 0;
}

.select__item {
  padding: 12px 15px 11px;
  cursor: pointer;

  &:hover {
    background-color: $select-item-active;
  }

  &--active {
    background-color: $select-item-active;
  }
}

.select__error {
  display: none;

  position: absolute;
  bottom: 0;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
