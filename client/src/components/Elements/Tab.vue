<script lang="ts" setup>
import { defineProps } from 'vue';

defineProps({
  title: { type: String, required: true },
  icon: { type: String, required: false } // Add icon prop
});

</script>

<template>
  <div class="border-b border-gray-200 dark:border-gray-700">
    <ul class="flex flex-wrap -mb-px text-sm font-medium text-center text-gray-500 dark:text-gray-400">
      <li class="me-2">
        <a href="#" class="inline-flex items-center justify-center p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300 group">
          <svg class="w-4 h-4 me-2 text-gray-400 group-hover:text-gray-500 dark:text-gray-500 dark:group-hover:text-gray-300" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
            <path :d="icon" />
          </svg>
          {{ title }}
        </a>
      </li>
    </ul>
  </div>

</template>
