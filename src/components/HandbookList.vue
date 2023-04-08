<template>
  <ul class="handbook-list">
    <li class="handbook-list__item handbook-list__title">{{ title }}</li>
    <li
      v-for="item in items"
      @click="handleOnClick(item)"
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
  methods: {
    handleOnClick(item) {
      this.$emit('itemClick', item);
    },
  },
};
</script>
