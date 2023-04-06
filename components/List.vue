<template>
  <nav class="min-h-0 flex-1 overflow-y-auto" aria-label="Directory">
    <div
      v-for="letter in Object.keys(directory)"
      :key="letter"
      class="relative"
    >
      <div
        class="sticky top-0 z-10 border-b border-t border-gray-200 bg-gray-50 px-6 py-1 text-sm font-medium text-gray-500"
      >
        <h3>{{ letter }}</h3>
      </div>
      <ul role="list" class="relative z-0 divide-y divide-gray-200">
        <li v-for="person in directory[letter]" :key="person.id">
          <div
            class="relative flex items-center space-x-3 px-6 py-5 focus-within:ring-2 focus-within:ring-inset focus-within:ring-pink-500 hover:bg-gray-50"
          >
            <div class="flex-shrink-0">
              <img
                class="h-10 w-10 rounded-full"
                :src="person.imageUrl"
                alt=""
              />
            </div>
            <div class="min-w-0 flex-1">
              <a href="#" class="focus:outline-none">
                <!-- Extend touch target to entire panel -->
                <span class="absolute inset-0" aria-hidden="true" />
                <p class="text-sm font-medium text-gray-900">
                  {{ person.name }}
                </p>
                <p class="truncate text-sm text-gray-500">{{ person.role }}</p>
              </a>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </nav>
</template>
          <script setup lang="ts">
</script>