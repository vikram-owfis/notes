<template>
  <div class="px-4 py-6 sm:p-8">
    <div class="grid max-w-2xl grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
      <div class="col-span-full">
        <label
          for="about"
          class="block text-sm font-medium leading-6 text-gray-900"
          >About</label
        >
        <div class="mt-2">
          <textarea
            v-model="input3"
            id="about"
            name="about"
            rows="3"
            class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6"
            placeholder="name"
          />
        </div>
        <div class="mt-2">
          <textarea
            v-model="input4"
            id="about"
            name="about"
            rows="3"
            class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6"
            placeholder="category"
          />
        </div>
        <p class="mt-3 text-sm leading-6 text-gray-600">
          Write a few sentences.
        </p>
        <button
          @click="editSaveCall()"
          class="ml-2 px-3 py-2 text-sm font-semibold text-white bg-green-600 rounded-md hover:bg-green-500 focus:outline-none focus:ring-2 focus:ring-red-600 focus:ring-opacity-50"
        >
          Save
        </button>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  data: {
    type: Object,
  },
});

const emit = defineEmits(["customPutemit"]);
let input3 = ref(props.data.name);
let input4 = ref(props.data.category);

const editSaveCall = async () => {
  console.log("propsdxdgdfgdfxdf-->", props.data);
  let body = {
    body: {
      name: props.input3.name,
      category: props.input4.category,
      page_html: null,
      page_css: null,
      is_published: true,
      last_published: null,
      meta_data: null,
      cdata1: null,
      cdata2: null,
      uid: props.data.uid,
    },
  };
  emit("customPutemit", body);
};
</script>