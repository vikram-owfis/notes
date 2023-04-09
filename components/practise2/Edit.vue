<template>
  <div>
    <div>
      <label
        for="first-name"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >enter your name</label
      >
      <div class="mt-2.5">
        <input
          v-model="updateData.name"
          type="text"
          name="first-name"
          id="first-name"
          autocomplete="given-name"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>
    <div>
      <label
        for="last-name"
        class="block text-sm font-semibold leading-6 text-gray-900"
        >description</label
      >
      <div class="mt-2.5">
        <input
          v-model="updateData.category"
          type="text"
          name="last-name"
          id="last-name"
          autocomplete="family-name"
          class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
      <div>
        <button
          @click="emit('editData')"
          type="submit"
          class="rounded bg-indigo-600 px-2 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
        >
          save
        </button>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref, defineProps, onMounted } from "vue";
const emit = defineEmits(["editData"]);

const props = defineProps({
  updateData: Object,
});
</script>