<script setup lang="ts">
import { ref } from 'vue';
import Tab from '@/components/Elements/Tab.vue';
import AddEmployee from '@/view/employees/AddEmployee.vue';
import ShowAllEmployees from '@/view/employees/ShowAllEmployees.vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const activeTab = ref<string| any>(route.params.tab || 'add-new-employee'); // Set a default value if 'tab' is not provided
const tabs: { title: string; tab: string; icon: string }[] = [
{
    title: "Add new employee",
    tab: "add-new-employee",
    icon: "M18 7.5h-.423l-.452-1.09.3-.3a1.5 1.5 0 0 0 0-2.121L16.01 2.575a1.5 1.5 0 0 0-2.121 0l-.3.3-1.089-.452V2A1.5 1.5 0 0 0 11 .5H9A1.5 1.5 0 0 0 7.5 2v.423l-1.09.452-.3-.3a1.5 1.5 0 0 0-2.121 0L2.576 3.99a1.5 1.5 0 0 0 0 2.121l.3.3L2.423 7.5H2A1.5 1.5 0 0 0 .5 9v2A1.5 1.5 0 0 0 2 12.5h.423l.452 1.09-.3.3a1.5 1.5 0 0 0 0 2.121l1.415 1.413a1.5 1.5 0 0 0 2.121 0l.3-.3 1.09.452V18A1.5 1.5 0 0 0 9 19.5h2a1.5 1.5 0 0 0 1.5-1.5v-.423l1.09-.452.3.3a1.5 1.5 0 0 0 2.121 0l1.415-1.414a1.5 1.5 0 0 0 0-2.121l-.3-.3.452-1.09H18a1.5 1.5 0 0 0 1.5-1.5V9A1.5 1.5 0 0 0 18 7.5Zm-8 6a3.5 3.5 0 1 1 0-7 3.5 3.5 0 0 1 0 7Z",
  },
  {
    title: "Show all employees",
    tab: "show-all-employees",
    icon: "M18 7.5h-.423l-.452-1.09.3-.3a1.5 1.5 0 0 0 0-2.121L16.01 2.575a1.5 1.5 0 0 0-2.121 0l-.3.3-1.089-.452V2A1.5 1.5 0 0 0 11 .5H9A1.5 1.5 0 0 0 7.5 2v.423l-1.09.452-.3-.3a1.5 1.5 0 0 0-2.121 0L2.576 3.99a1.5 1.5 0 0 0 0 2.121l.3.3L2.423 7.5H2A1.5 1.5 0 0 0 .5 9v2A1.5 1.5 0 0 0 2 12.5h.423l.452 1.09-.3.3a1.5 1.5 0 0 0 0 2.121l1.415 1.413a1.5 1.5 0 0 0 2.121 0l.3-.3 1.09.452V18A1.5 1.5 0 0 0 9 19.5h2a1.5 1.5 0 0 0 1.5-1.5v-.423l1.09-.452.3.3a1.5 1.5 0 0 0 2.121 0l1.415-1.414a1.5 1.5 0 0 0 0-2.121l-.3-.3.452-1.09H18a1.5 1.5 0 0 0 1.5-1.5V9A1.5 1.5 0 0 0 18 7.5Zm-8 6a3.5 3.5 0 1 1 0-7 3.5 3.5 0 0 1 0 7Z",
  },
];

const switchTab = (tab: string): void => {
  activeTab.value = tab;
};

const getComponent = (tab: string): object | null => {
  switch (tab) {
    case 'add-new-employee':
      return AddEmployee;
    case 'show-all-employees':
      return ShowAllEmployees;
    default:
      return null;
  }
};
</script>


<template>
  <div>
    <div class="flex flex-wrap -mb-px text-sm font-medium text-center text-gray-500 dark:text-gray-400">
      <Tab
        v-for="item in tabs"
        :key="item.tab"
        :value="item.tab"
        :title="item.title"
        :icon="item.icon"
        @click="switchTab(item.tab)"
        :active="activeTab === item.tab"
      />
    </div>

    <div v-for="tabItem in tabs" :key="tabItem.tab" class="mt-5 disable-tab-transition">
      <div v-if="activeTab === tabItem.tab">
      <div class="grid grid-cols-12">
        <div class="col-span-12">
          <component :is="getComponent(tabItem.tab)" />
        </div>
      </div>
    </div>
  </div>
  </div>
</template>
