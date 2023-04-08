<template>
  <HandBook title="Статус поставки" :items="dataSet1" v-model:active-item="dataSetAcive1" />
</template>

<script>
import HandBook from './components/Handbook.vue';

export default {
  name: 'App',
  components: {
    HandBook,
  },
  data() {
    return {
      dataSet1: [
        {
          code: 0,
          description: 'Формируется',
        },
        {
          code: 10,
          description: 'Товар прибыл',
        },
        {
          code: 20,
          description: 'Товар прибыл (срочная поставка)',
        },
        {
          code: 30,
          description: 'Оформление ДТ',
        },
        {
          code: 40,
          description: 'ДТ выпущена',
        },
        {
          code: 50,
          description: 'Поставка закрыта',
        },
      ],
      dataSetAcive1: null,
    };
  },
  created() {
    this.dataSetAcive1 = { ...this.dataSet1[0] };
  },
};
</script>

<style></style>
