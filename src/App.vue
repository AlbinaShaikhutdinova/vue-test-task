<template>
  <div class="container">
    <HandBook title="Статус поставки" :items="dataSetStatus" v-model:active-item="activeStatus" />
    <HandBook title="Режим перемещения" :items="dataSetMode" v-model:active-item="activeMode" />
  </div>
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
      dataSetStatus: [
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
      dataSetMode: [
        {
          id: 1,
          description: 'Импорт',
        },
        {
          id: 2,
          description: 'Экспорт',
        },
      ],

      activeStatus: null,
      activeMode: null,
    };
  },
  created() {
    this.activeStatus = { ...this.dataSetStatus[0] };
    this.activeMode = { ...this.dataSetMode[0] };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
.container {
  padding: 40px;
  display: flex;
  gap: 20px;
}
</style>
