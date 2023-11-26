<script setup lang="ts">
import { ref } from "vue";
import ModelConfirm from "../components/Common/ModelConfirm.vue";

const yourMessage = ref("");
const modalIsOpen = ref(false);

const openModal = () => {
  yourMessage.value = "Are you sure you want to delete this product?";
  modalIsOpen.value = true;
};

const handleConfirm = () => {
  console.log("User confirmed");
  modalIsOpen.value = false;
};
</script>

<template>
  <div>
    <ModelConfirm :message="yourMessage" :is-open="modalIsOpen"
     @update:is-open="modalIsOpen = $event" @confirm="handleConfirm" />
    <button @click="openModal">Open Modal</button>
  </div>
</template>

