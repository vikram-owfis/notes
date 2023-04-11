<template>
  <div>
    <button
      @click="openModal()"
      type="button"
      class="mt-2 bg-indigo-600 text-white py-3 px-6 rounded-md shadow-sm hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-600 mx-auto block"
    >
      Add Contact
    </button>

    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10">
        <TransitionChild
          as="template"
          enter="ease-out duration-300"
          enter-from="opacity-0"
          enter-to="opacity-100"
          leave="ease-in duration-200"
          leave-from="opacity-100"
          leave-to="opacity-0"
        >
          <div
            class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
          />
        </TransitionChild>

        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div
            class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
          >
            <TransitionChild
              as="template"
              enter="ease-out duration-300"
              enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
              enter-to="opacity-100 translate-y-0 sm:scale-100"
              leave="ease-in duration-200"
              leave-from="opacity-100 translate-y-0 sm:scale-100"
              leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
            >
              <DialogPanel
                class="relative transform overflow-hidden rounded-lg bg-white px-4 pt-5 pb-4 text-left shadow-xl transition-all sm:my-8 sm:max-w-fit sm:max-w-4xl sm:p-4"
              >
                <div class="sm:divide-y-0 sm:gap-px sm:grid">
                  <div class="border m-auto p-4">
                    <div class="px-4 sm:px-6 lg:px-8">
                      <div class="sm:flex sm:items-center"></div>
                      <div class="mt-8 flow-root">
                        <div
                          class="-my-2 -mx-4 overflow-x-auto sm:-mx-6 lg:-mx-8"
                        >
                          <div class="ml-4 text-lg text-gray-900">
                            <h3 class="flex">
                              <svg
                                xmlns="http://www.w3.org/2000/svg"
                                fill="none"
                                viewBox="0 0 24 24"
                                stroke-width="1.5"
                                stroke="currentColor"
                                class="w-6 h-6"
                              >
                                <path
                                  stroke-linecap="round"
                                  stroke-linejoin="round"
                                  d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L10.582 16.07a4.5 4.5 0 01-1.897 1.13L6 18l.8-2.685a4.5 4.5 0 011.13-1.897l8.932-8.931zm0 0L19.5 7.125M18 14v4.75A2.25 2.25 0 0115.75 21H5.25A2.25 2.25 0 013 18.75V8.25A2.25 2.25 0 015.25 6H10"
                                />
                              </svg>
                              Add Contact
                            </h3>
                          </div>
                          <div class="border-b border-gray-400"></div>

                          <div>
                            <div class="flex flex-row-reverse gap-8">
                              <div class="sm:col-span-3">
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

                              <div class="sm:col-span-3">
                                <label
                                  for="first-name"
                                  class="block text-sm font-semibold leading-6 text-gray-900"
                                  >phone</label
                                >
                                <div class="mt-2">
                                  <input
                                    v-model="fourth"
                                    type="number"
                                    name="first-name"
                                    id="first-name"
                                    autocomplete="given-name"
                                    class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                                  />
                                </div>
                              </div>
                              <UserDetails class="mr-96" />
                            </div>
                          </div>
                          <div>
                            <label
                              for="cars"
                              class="block text-sm font-semibold leading-6 text-gray-900"
                              >Country:</label
                            >
                            <div class="mt-2 relative rounded-md shadow-sm">
                              <select
                                v-model="last"
                                name="cars"
                                id="cars"
                                class="block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md"
                              >
                                <option value="india">INDIA</option>
                                <option value="pakistan">PAKISTAN</option>
                                <option value="australia">AUSTRALIA</option>
                                <option value="china">CHINA</option>
                              </select>
                              <div
                                class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none"
                              ></div>
                            </div>
                          </div>
                          <div
                            class="mt-4 px-8 flex justify-between items-center"
                          >
                            <button
                              type="button"
                              @click="open = false"
                              class="bg-red-600 py-1 px-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                            >
                              back
                            </button>

                            <div class="flex">
                              <button
                                type="button"
                                class="bg-gray-600 mr-12 py-1 px-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                              >
                                Edit
                              </button>

                              <button
                                type="submit"
                                @click.prevent="send"
                                @click="open = false"
                                class="bg-indigo-600 py-1 px-2 text-sm font-semibold text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                              >
                                Save
                              </button>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
                <br />
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </div>
</template>

<script setup>
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
import { ref } from "vue";

import { defineEmits } from "vue";

const open = ref(false);
const firsht = ref("");
const fourth = ref("");
const third = ref("");
const last = ref("");
const change = ref("");
const emit = defineEmits(["inputData", "change"]);

function send() {
  emit("inputData", {
    name: firsht,
    subject: fourth,
    body: third,
    category: last,
  });
}
function openModal() {
  open.value = !open.value;
}
</script>
