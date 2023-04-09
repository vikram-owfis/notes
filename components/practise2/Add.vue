<template>
  <div
    class="mx-auto mt-8 grid max-w-3xl grid-cols-1 gap-6 sm:px-6 lg:max-w-7xl"
  >
    <h1 class="font-semibold leading-6 text-gray-900 mb-3 text-2xl">
      Candidates
    </h1>
    <div class="space-y-6 lg:col-span-2 lg:col-start-1">
      <section aria-labelledby="notes-title">
        <div class="bg-white shadow sm:overflow-hidden sm:rounded-lg">
          <div class="divide-y divide-gray-200">
            <div class="px-4 py-5 sm:px-6">
              <h2 id="notes-title" class="text-lg font-medium text-gray-900">
                Mock interviews
              </h2>
            </div>
          </div>
        </div>
      </section>
    </div>

    <div>
      <form
        action="#"
        method="POST"
        class="px-6 pb-24 pt-20 sm:pb-32 lg:px-8 lg:py-48"
      >
        <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
          <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
            <div>
              <label
                for="first-name"
                class="block text-sm font-semibold leading-6 text-gray-900"
                >enter your name</label
              >
              <div class="mt-2.5">
                <input
                  v-model="firsht"
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
                  v-model="last"
                  type="text"
                  name="last-name"
                  id="last-name"
                  autocomplete="family-name"
                  class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                />
              </div>
              <div>
                <button
                  @click.prevent="send"
                  type="submit"
                  class="rounded bg-indigo-600 px-2 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                >
                  save
                </button>
              </div>
            </div>
          </div>
        </div>
      </form>
      <div></div>
    </div>
  </div>
</template>
<script setup >
import { ref } from "vue";
import { defineEmits } from "vue";
const firsht = ref("");
const last = ref("");
const emit = defineEmits(["inputData"]);
function send() {
  emit("inputData", { name: firsht, category: last });
  console.log("inputData", inputData);
}
</script>