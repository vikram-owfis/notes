<template>
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
              Save
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
</template>