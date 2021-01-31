<template>
  <div class="select">
    <p class="select__label">{{ select.label }}</p>
    <div class="select__inner">
      <div
          class="select__placeholder"
          tabindex="0"
          :class="{'select__placeholder--selected' : select.change}"
          @click="toggleList"
      >{{ select.placeholder }}</div>
      <ul
          class="select__list"
          v-if="openList"
      >
        <li class="select__item"
            v-for="(item, itemIndex) in select.options"
            :key="itemIndex"
            :class="{'select__item--active' : item.active}"
            @click="onSelectItem(itemIndex)"
        >{{ item.text }}</li>
      </ul>
    </div>
    <span
        class="select__error"
        v-if="select.change && !select.valid"
    >{{ select.error }}</span>
  </div>
</template>

<script>
export default {
  name: "Select",
  props: {
    select: Object,
    selectIndex: Number
  },
  data () {
    return {
      openList: false
    }
  },
  methods: {
    toggleList () {
      this.openList = !this.openList;
      this.$emit('change', this.selectIndex);
    },
    onSelectItem (itemIndex) {
      this.openList = false;
      this.$emit('selected', itemIndex, this.selectIndex);
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";

.select {
  position: relative;
  width: 100%;
  padding-bottom: 30px;
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
    top: 16px;
    right: 19px;
    width: 12px;
    height: 12px;
    border-left: 2px solid $input-border-focus-color;
    border-bottom: 2px solid $input-border-focus-color;
    transform: rotate(-45deg);
  }

  &:focus {
    outline: none;
    border: 2px solid $input-border-focus-color;
    padding: 14px 56px 13px 15px;

    &::after {
      top: 15px;
      right: 18px;
    }
  }

  &:hover {
    border: 2px solid $input-border-focus-color;
    padding: 14px 56px 13px 15px;
    color: $text-main;

    &::after {
      top: 15px;
      right: 18px;
    }
  }

  &--selected {
    color: $text-main;
  }
}

.select__list {
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
  z-index: 1;
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
  position: absolute;
  bottom: 14px;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
