<template>
  <div class="component">
    <label :for="item">{{ item }}<sup>*</sup></label>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "InputComponent",
  props: ["item"],
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.component {
  display: flex;
  flex-direction: column;
  label {
    color: #204379;
    font-size: 16px;
    line-height: 140%;
    font-weight: 400;
    sup {
      color: #b57556;
    }
  }
}
</style>
