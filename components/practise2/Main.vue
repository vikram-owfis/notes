<template>
  <div>
    <div>
      <Practise2Add @inputData="inputData" />
      <Practise2List :details="employeeDetails" @edit="edit" />
      <Practise2Edit
        v-if="isEdit"
        :key="render"
        :updateData="editPrefilledData"
        @editData="saved"
      />
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";
const details = ref("");
const open = ref("false");
const editRender = ref(0);
const render = ref(0);
const isEdit = ref(false);
const updateData = ref({});
const editPrefilledData = ref("");
const editIndex = ref(0);
const edit = (editData: any, index: number) => {
  console.log("haiiiii");
  editPrefilledData.value = editData;
  editRender.value++;
  editIndex.value = index;
  isEdit.value = true;
};
//getItems from localStorage
onMounted(() => {
  const employeeStoredData = localStorage.getItem("employeeData");
  if (employeeStoredData) {
    employeeDetails.value = JSON.parse(employeeStoredData);
  }
});
const employeeDetails = ref([]);
//setItems in localStorage when new record is added
const inputData = (details: any) => {
  employeeDetails.value.push(details);
  localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
};
const saved = (editDetails: any) => {
  employeeDetails.value[editIndex.value] = editDetails;
  localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
};

const deleteEmployee = (index: number) => {
  employeeDetails.value.splice(index, 1);
  localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
};
</script>