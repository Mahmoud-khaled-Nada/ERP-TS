<script lang="ts" setup>
import { ref } from "vue";

interface User {
  username: string;
  email: string;
  password: string;
  confirm: string;
}

const user = ref<User>({
  username: "",
  email: "",
  password: "",
  confirm: "",
});

const register = () => {
  const data = JSON.parse(JSON.stringify(user.value));
  console.log("Registered: ", data);
};
</script>
<template>
  <div class="mt-3">
    <div class="mt-4">
      <div class="p-6 bg-white rounded-md shadow-md">
        <h2 class="text-lg font-semibold text-gray-700 capitalize">Add A New Employee</h2>

        <form @submit.prevent="register">
          <div class="grid grid-cols-1 gap-6 mt-4 sm:grid-cols-3">
            <div>
              <label class="text-gray-700">Username</label>
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="text"
                v-model="user.username"
              />
            </div>

            <div>
              <label class="text-gray-700"
                >Email Address</label
              >
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="email"
                v-model="user.email"
              />
            </div>

            <div>
              <label class="text-gray-700">Password</label>
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="password"
                v-model="user.password"
              />
            </div>

            <div>
              <label class="text-gray-700" 
                >Password Confirmation</label
              >
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="password"
                v-model="user.confirm"
              />
            </div>

            <div>
              <label class="text-gray-700"
                >Password Confirmation</label
              >
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="password"
                v-model="user.confirm"
              />
            </div>
            <div>
              <label class="text-gray-700" 
                >Password Confirmation</label
              >
              <input
                class="w-full mt-2 border-gray-200 rounded-md focus:border-indigo-600 focus:ring focus:ring-opacity-40 focus:ring-indigo-500"
                type="password"
                v-model="user.confirm"
              />
            </div>
          </div>

          <div class="flex justify-end mt-4">
            <button
              class="px-4 py-2 text-gray-200 bg-gray-800 rounded-md hover:bg-gray-700 focus:outline-none focus:bg-gray-700"
            >
              Save
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
