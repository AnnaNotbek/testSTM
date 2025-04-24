<script setup>
import { ref } from "vue";
const label = ref("Статус поставки");

const items = [
  { value: 0, title: "Формируется" },
  { value: 10, title: "Товар прибыл" },
  { value: 20, title: "Товар прибыл (срочная поставка)" },
  { value: 30, title: "Оформление ДТ" },
  { value: 40, title: "ДТ выпущена" },
  { value: 50, title: "Поставка закрыта" },
];

console.log(label.value);
</script>

<template>
  <v-select class="custSelect" :label="label" clearable :items="items">
  </v-select>
</template>

<style scoped>
.custSelect {
  max-width: 500px;
}
</style>
