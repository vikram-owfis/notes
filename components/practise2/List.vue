<template>
  <div>
    <div v-for="(detail, index) in details" :key="index">
      <table class="w-full table-auto">
        <thead>
          <tr>
            <th class="px-4 py-2 text-left">Name</th>
            <th class="px-4 py-2 text-left">Category</th>
            <th class="px-4 py-2 text-left">Actions</th>
          </tr>
        </thead>
        <tbody>
          <tr class="bg-gray-100">
            <td class="px-4 py-2">{{ detail.name }}</td>
            <td class="px-4 py-2">{{ detail.category }}</td>
            <td class="px-4 py-2">
              <button
                @click="editData(detail, index)"
                class="px-3 py-2 text-sm font-semibold text-white bg-blue-600 rounded-md hover:bg-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-opacity-50"
              >
                Edit
              </button>
              <button
                @click="deleteData(detail)"
                class="ml-2 px-3 py-2 text-sm font-semibold text-white bg-red-600 rounded-md hover:bg-red-500 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-opacity-50"
              >
                Delete
              </button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineEmits, defineProps } from "vue";
const props = defineProps({
  details: {
    type: Array,
  },
});
const deleteData = async (id: any) => {
  const deleteOptions = {
    method: "DELETE",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
  };

  await useAuthLazyFetchDelete(
    `https://v1-orm-lib.mars.hipso.cc/api/pages/${id.uid}`,
    deleteOptions
  );
};
</script>