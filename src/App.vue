<script setup>
import userHandbookComposition from "./components/userHandbookComposition.vue";
import { ref } from "vue";

const status = ref([
  { value: 0, title: "Формируется" },
  { value: 10, title: "Товар прибыл" },
  { value: 20, title: "Товар прибыл (срочная поставка)" },
  { value: 30, title: "Оформление ДТ" },
  { value: 40, title: "ДТ выпущена" },
  { value: 50, title: "Поставка закрыта" },
]);

const mode = ref([
  {
    value: "import",
    title: "импорт",
  },
  {
    value: "export",
    title: "экспорт",
  },
]);

const selectedStatus = ref({});
const selectedMode = ref({});

</script>

<template>
  <div class="layout">
    <userHandbookComposition
      v-model="selectedStatus"
      descriptionKey="title"
      :items="status"
      label="Статус поставки"
    />
    <userHandbookComposition
      v-model="selectedMode"
      descriptionKey="title"
      :items="mode"
      label="Режим перемещения"
    />
  </div>
</template>

<style scoped lang="css">
.layout {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
}
</style>
