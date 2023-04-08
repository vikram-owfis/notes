<template>
  <div>
    <div v-for="(detail, index) in details" :key="index">
      <div class="bg-white shadow-md rounded-md p-4">
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
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from "vue";
const props = defineProps({
  details: {
    type: Array,
  },
});
const emit = defineEmits(["editdata"]);

const editData = (detail: any, index: any) => {
  // const editOptions = {
  //   method: "PUT",
  //   headers: {
  //     "Content-Type": "application/json",
  //     Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiNmZlZDJiYTgwYThkNGM0MjlhZGZiOGQ1ZTZmZTY0ODAiLCJkIjoiMTY4MDA4NCIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzk3Mjl9.5cJkrudAvTWoVRigTNcfQ321W_lOyMm-xsb9rMxuVBE`,
  //   },
  // };
  // const editTemplateData = useAuthLazyFetchPut(
  //   `https://v1-orm-lib.mars.hipso.cc/api/pages/${id.uid}`,
  //   editOptions
  // );
  emit("editdata", detail, index);
};
</script>

<style scoped></style>
