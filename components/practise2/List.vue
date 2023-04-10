<template>
  <div class="grid grid-cols-4 gap-4 border shadow-md mt-9">
    <div v-for="(detail, index) in details" :key="index">
      <div class="flex flex-col">
        <div>
          <div>
            <div>
              <div class="border shadow-md p-4 card">
                <div class="grid grid-cols-3 gap-4">
                  <div class="px-6 py-4 col-span-3">
                    <div class="text-gray-600 text-sm">
                      country: {{ detail.category }}
                    </div>
                    <div class="text-gray-600 text-sm">
                      name: {{ detail.name }}
                    </div>
                    <div class="text-gray-600 text-sm mb-2">
                      phone number: {{ detail.subject }}
                    </div>
                  </div>

                  <div class="flex items-center">
                    <button
                      @click="emits('edit', detail, index)"
                      class="px-3 py-2 bg-gray-600 mr-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 text-sm font-semibold text-white bg-blue-600 rounded-md hover:bg-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-opacity-50"
                    >
                      Edit
                    </button>
                    <button
                      @click="deleteData(index)"
                      class="px-3 bg-gray-600 mr-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 py-2 text-sm font-semibold text-white bg-red-600 rounded-md hover:bg-red-500 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-opacity-50"
                    >
                      Delete
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
          <div
            class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8"
          >
            <div
              class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg"
            >
              <div
                class="bg-white rounded-lg shadow-md overflow-hidden border-dashed border-2 p-4"
              >
                <div class="grid grid-cols-3 gap-4">
                  <div class="px-6 py-4 col-span-3">
                    <div class="font-semibold text-lg mb-2">
                      name :{{ detail.name }}
                    </div>
                    <div class="text-gray-600 text-sm mb-2">
                      phone number :{{ detail.subject }}
                    </div>
                    <div class="text-gray-600 text-sm">
                      country :{{ detail.category }}
                    </div>
                  </div>

                  <div class="flex items-center">
                    <button
                      @click="emits('edit', detail)"
                      class="px-3 py-2 bg-gray-600 mr-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 text-sm font-semibold text-white bg-blue-600 rounded-md hover:bg-blue-500 focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-opacity-50"
                    >
                      Edit
                    </button>
                    <button
                      @click="deleteData(detail)"
                      class="px-3 bg-gray-600 mr-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 py-2 text-sm font-semibold text-white bg-red-600 rounded-md hover:bg-red-500 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-opacity-50"
                    >
                      Delete
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div> -->
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineEmits, defineProps, ref } from "vue";
const props = defineProps({
  details: {
    type: Array,
  },
});

const emits = defineEmits(["edit", "deleteData"]);
</script>