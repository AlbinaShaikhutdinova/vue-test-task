<template>
  <ul class="handbook-list">
    <li class="handbook-list__item handbook-list__title">
      {{ title }} <span class="handbook-list__close" @click="handleOnCloseClick"></span>
    </li>
    <li
      v-for="item in items"
      @click="handleOnItemClick(item)"
      :key="item.code"
      class="handbook-list__item"
    >
      {{ item.description }}
    </li>
  </ul>
</template>
<script>
export default {
  name: 'HandbookList',
  props: {
    title: String,
    items: Array,
  },
  emits: ['itemClick', 'close'],
  methods: {
    handleOnItemClick(item) {
      this.$emit('itemClick', item);
    },
    handleOnCloseClick() {
      this.$emit('close');
    },
  },
};
</script>
<style lang="scss">
.handbook-list {
  list-style: none;
  margin: 0;
  padding: 0;
  box-shadow: 0px 8px 10px 2px rgba(34, 60, 80, 0.2);
  overflow-y: scroll;
  &__item {
    padding: 5px;
    border-bottom: 2px solid #cfcfcf;
    cursor: pointer;
    &:last-child {
      border: none;
    }
  }
  &__title {
    position: relative;
    padding-right: calc(1.2em + 5px);
    font-weight: 600;
    cursor: auto;
  }
  &__close {
    position: absolute;
    display: block;
    width: 1.2em;
    height: 1.2em;
    top: 50%;
    right: 5px;
    transform: translateY(-50%);
    cursor: pointer;
  }
  &__close:before,
  &__close:after {
    display: block;
    content: '';
    width: 2px;
    background-color: #333333;
    height: 100%;
    position: absolute;
    top: 0;
    left: 50%;
  }
  &__close:before {
    transform: rotate(45deg);
  }
  &__close:after {
    transform: rotate(-45deg);
  }
}
</style>
