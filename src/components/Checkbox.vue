<template>
  <div class="checkbox">
    <input
        :id=checkbox.id
        :name="checkbox.name"
        :type=checkbox.type
        class="checkbox__field visually-hidden"
        @change="onCheck"
        v-model="checked"
    >
    <label :for=checkbox.id class="checkbox__label" v-html="checkbox.label"></label>
    <span
        class="checkbox__error"
        v-if="checkbox.change && !checkbox.valid"
    >{{ checkbox.error }}</span>
  </div>
</template>

<script>
export default {
  name: "Checkbox",
  props: {
    checkbox: Object,
    checkboxIndex: Number
  },
  data () {
    return {
      checked: false
    }
  },
  methods: {
    onCheck () {
      this.$emit('change', this.checked, this.checkboxIndex);
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/variables";
@import "src/assets/styles/helpers";

.checkbox {
  position: relative;
  padding-bottom: 42px;
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
  box-shadow: $checkbox-shadow-focus;
}

.checkbox__link {
  color: $text-blue;

  &:hover {
    color: $text-light-blue;
  }
}

.checkbox__error {
  position: absolute;
  bottom: 16px;
  left: 0;
  font-size: 14px;
  line-height: 18px;
  color: $text-error;
}
</style>
