<script setup>
import { ref } from "vue";

const chosedItem = ref();

const props = defineProps(["items", "label", "modelValue", "descriptionKey"]);

const emit = defineEmits();

const isOpenDropdown = ref(false);

function showDropdown() {
  isOpenDropdown.value = !isOpenDropdown.value;
}

function closeDropdown() {
  isOpenDropdown.value = false;
}

function handleFocus() {
  isOpenDropdown.value = true;
}

function choseItem(item) {
  chosedItem.value = item.title;
  emit("update:modelValue", item);
  isOpenDropdown.value = !isOpenDropdown.value;
}
</script>

<template>
  <div class="select">
    <div class="selectStyled" @click="showDropdown">
      <h4>{{ label }}</h4>
      <input
        class="selectInput"
        @focus="handleFocus"
        :value="modelValue ? modelValue[descriptionKey] : ''"       
        readonly
        />
    </div>
    <div v-show="isOpenDropdown" class="dropdown">
      <div class="dropdownLabel">
        <h5>{{ label }}</h5>
        <button @click="showDropdown">x</button>
      </div>
      <div v-for="item in items" :key="item.value">
        <div class="dropdownItem" @click="choseItem(item)">
          {{ item[descriptionKey] }}
        </div>
      </div>
    </div>
    <div v-if="isOpenDropdown" class="overlay" @click="closeDropdown"></div>
  </div>
</template>

<style lang="css">
.select {
  margin: 20px;
}

.selectStyled {
  border: 1px solid #000;
  width: 400px;
  padding: 5px;
}

.selectInput {
  width: 100%;
  outline: none;
}

.dropdown {
  position: absolute;
  border: 1px solid #000;
  z-index: 50;
}

.dropdownLabel {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px;
  border-bottom: 1px solid #000;
}

.dropdownItem {
  padding: 5px;
}
.dropdownItem:hover {
  background-color: rgb(179, 179, 179);
}
.dropdownItem:active {
  background-color: rgb(119, 119, 119);
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: transparent;
  z-index: 5;
}
</style>
