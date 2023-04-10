<template>
  <div>
   
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
                          >Exam</DialogTitle
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
                                  for="first-name"
                                  class="block text-sm font-semibold leading-6 text-gray-900"
                                  >subject</label
                                >

                                <div class="mt-2.5">
                                  <input
                                    v-model="updateData.subject"
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
                                    v-model="updateData.body"
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
    </TransitionRoot> -->
    <TransitionRoot as="template" :show="open">
      <Dialog as="div" class="relative z-10" @close="openModal">
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
                <!--
                regularization
            -->

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
                              Edit contact
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
                                    v-model="updateData.name"
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
                                    v-model="updateData.subject"
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
                                v-model="updateData.category"
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
                            <div class="flex">
                              <button
                                @click="editData"
                                @click.prevent="send"
                                type="submit"
                                class="mt-2 w-32 rounded bg-indigo-600 px-2 py-1 text-xs font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 ml-2"
                              >
                                save
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
import { ref, defineProps, defineEmits } from "vue";
const open = ref(true);
const change = ref("");
const emit = defineEmits(["editData", "change"]);
const props = defineProps({
  updateData: Array,
});
function openModal() {
  open.value = !open.value;
}

const editData = () => {
  emit("editData", updateData);
  open.value = false;
};
</script>

