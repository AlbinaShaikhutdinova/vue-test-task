<template>
  <div class="handbook-input">
    <span class="handbook-input__title">{{ title }}</span>
    <input
      readonly
      type="text"
      @click="handleOnFocus"
      @focus="handleOnFocus"
      class="handbook-input__element"
      :value="value"
    />
  </div>
</template>
<script>
export default {
  name: 'HandbookInput',
  props: {
    title: String,
    value: String,
  },
  emits: ['focus'],
  methods: {
    handleOnFocus() {
      this.$emit('focus');
    },
  },
};
</script>
<style lang="scss">
.handbook-input {
  position: relative;
  width: 100%;
  &__title {
    position: absolute;
    top: 5px;
    left: 5px;
    font-size: 12px;
    font-weight: 700;
    display: block;
  }
  &__element {
    padding: 20px 5px 5px;
    width: 100%;
    border: 1px solid #36d836;
    font-size: 14px;
    &:focus {
      outline: none;
      box-shadow: 0px 0px 6px 1px rgba(54, 216, 54, 0.7);
    }
  }
}
</style>
