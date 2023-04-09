<template>
  <div>
    <button
      @click="open = true"
      type="button"
      class="mt-2 bg-indigo-600 text-white py-3 px-6 rounded-md shadow-sm hover:bg-indigo-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-600 mx-auto block"
    >
      Add Lead
    </button>

    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="open = false">
        <div class="fixed inset-0" />

        <div class="fixed inset-0 overflow-hidden">
          <div class="absolute inset-0 overflow-hidden">
            <div
              class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
            >
              <TransitionChild
                as="template"
                enter="transform transition ease-in-out duration-500 sm:duration-700"
                enter-from="translate-x-full"
                enter-to="translate-x-0"
                leave="transform transition ease-in-out duration-500 sm:duration-700"
                leave-from="translate-x-0"
                leave-to="translate-x-full"
              >
                <DialogPanel class="pointer-events-auto w-screen max-w-md">
                  <div
                    class="flex h-full flex-col overflow-y-scroll bg-white shadow-xl"
                  >
                    <div class="bg-indigo-700 px-4 py-6 sm:px-6">
                      <div class="flex items-center justify-between">
                        <DialogTitle
                          class="text-base font-semibold leading-6 text-white"
                          >email templates</DialogTitle
                        >
                        <div class="ml-3 flex h-7 items-center">
                          <button
                            type="button"
                            class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white"
                            @click="open = false"
                          >
                            <span class="sr-only">Close panel</span>
                            <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                          </button>
                        </div>
                      </div>
                    </div>
                    <div class="relative flex-1 px-4 py-6 sm:px-6">
                      <div>
                        <form
                          action="#"
                          method="POST"
                          class="px-6 pb-24 pt-20 sm:pb-32 lg:px-8 lg:py-48"
                        >
                          <div class="mx-auto max-w-xl lg:mr-0 lg:max-w-lg">
                            <div
                              class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2"
                            >
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
                                  for="first-name"
                                  class="block text-sm font-semibold leading-6 text-gray-900"
                                  >subject</label
                                >

                                <div class="mt-2.5">
                                  <input
                                    v-model="fourth"
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
                                  for="first-name"
                                  class="block text-sm font-semibold leading-6 text-gray-900"
                                  >body</label
                                >

                                <div class="mt-2.5">
                                  <input
                                    v-model="third"
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

                                <button
                                  @click.prevent="send"
                                  type="submit"
                                  class="mt-2 w-32 rounded bg-indigo-600 px-2 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 ml-2"
                                >
                                  save
                                </button>
                              </div>
                            </div>
                          </div>
                        </form>
                      </div>
                    </div>
                  </div>
                </DialogPanel>
              </TransitionChild>
            </div>
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

const emit = defineEmits(["inputData"]);

function send() {
  emit("inputData", {
    name: firsht,
    subject: fourth,
    body: third,
    category: last,
  });
}
</script>