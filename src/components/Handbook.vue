<template>
  <div class="handbook" :class="isSelectActive ? 'open' : ''">
    <input
      type="text"
      @click="setListState(true)"
      @focus="setListState(true)"
      class="handbook__input"
      :value="activeItem.description"
    />
    <HandbookList
      class="handbook__list"
      :title="shortTitle"
      :items="items"
      @itemClick="updateActiveItem"
      @close="setListState(false)"
    />
  </div>
  <div @click="setListState(false)" class="handbook__layover"></div>
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
  data() {
    return {
      isSelectActive: false,
    };
  },
  computed: {
    shortTitle() {
      return this.title.split(' ')[0];
    },
  },
  methods: {
    updateActiveItem(item) {
      this.$emit('update:activeItem', item);
      this.setListState(false);
    },
    setListState(state) {
      this.isSelectActive = state;
    },
  },
};
</script>
<style lang="scss">
.handbook {
  max-width: 260px;
  width: 100%;
  position: relative;
  z-index: 1;
  &__input {
    width: 100%;
  }
  &__list {
    display: none;
    width: 100%;
    max-height: 160px;
    transform: translateY(5px);
  }
  &__layover {
    display: none;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    z-index: 0;
  }
  &.open &__list,
  &.open + &__layover {
    display: block;
  }
}
</style>
