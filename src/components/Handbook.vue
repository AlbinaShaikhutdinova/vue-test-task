<template>
  <div class="handbook">
    <input type="text" class="handbook__input" :value="activeItem.description" />
    <HandbookList :title="shortTitle" :items="items" @itemClick="updateActiveItem" />
  </div>
</template>
<script>
import HandbookList from './HandbookList.vue';
export default {
  name: 'HandBook',
  components: {
    HandbookList,
  },
  props: {
    title: String,
    items: Array,
    activeItem: {
      type: Object,
    },
  },
  emits: ['update:activeItem'],
  computed: {
    shortTitle() {
      return this.title.split(' ')[0];
    },
  },
  methods: {
    updateActiveItem(item) {
      this.$emit('update:activeItem', item);
    },
  },
};
</script>
