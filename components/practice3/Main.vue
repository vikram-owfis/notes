<template>
  <div>
    <div class="min-h-full">
      <div
        class="mx-auto mt-8 grid max-w-3xl grid-cols-1 gap-6 sm:px-6 lg:max-w-7xl"
      >
        <practice3List @openModal="editModal" @deleteNotes="deleteNotes" />
        <practice3Add @postData="postData" />
        <div v-if="openModal">
          <practice3Edit
            @putData="putData"
            :filled_note="prefilledData"
            :uid="prefilledDataUId"
          />
        </div>
      </div>
    </div>
  </div>
</template>
    <script setup lang="ts">
import { ref, defineProps } from "vue";
const props = defineProps({
  notesValue: {
    type: String,
  },
});
const openModal = ref(false);
const prefilledData = ref("");
const prefilledDataUId = ref("");
const note = ref("");
const getData = await useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/notes/entity/TASKS/1360?project_id=111&offset=0&limit=100&sort_column=id&sort_direction=desc",
  ""
);
note.value = getData.data._rawValue;
async function putData(prefilledNote: any) {
  let body = {
    entity_id: "1360",
    project_id: "111",
    note: prefilledNote.value,
    entity: "TASKS",
    uid: prefilledDataUId.value,
  };
  const { data: items, pending } = await useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/notes/${prefilledDataUId.value}`,
    { body: JSON.stringify(body) }
  );
  note.value.forEach((item: any, index: any) => {
    if (item.uid == prefilledDataUId.value) {
      item.note = prefilledNote.value;
    }
  });
}
function editModal(value: any) {
  openModal.value = true;
  prefilledData.value = value.prefilledData._rawValue;
  prefilledDataUId.value = value.prefilledDataUId._rawValue;
}
async function postData(notesValue) {
  const postoptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiOWRmODYxZWMyYzc1NDA5N2FhMDJiZDEzYTQ2YTZlODgiLCJkIjoiMTY4MDA5NSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODcxODB9.9Nf-OXN_wI59DptM0x_wCgQIPMJKe0Ud5lUprHXQFgg`,
    },
    body: {
      entity_id: "1360",
      project_id: "111",
      note: notesValue,
      entity: "TASKS",
    },
  };
  const data = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/notes/TASKS/1360",
    postoptions
  );
}
function deleteNotes(id: any) {
  const deleteOptions = {
    method: "DELETE",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization: ` "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiOWRmODYxZWMyYzc1NDA5N2FhMDJiZDEzYTQ2YTZlODgiLCJkIjoiMTY4MDA5NSIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyODcxODB9.9Nf-OXN_wI59DptM0x_wCgQIPMJKe0Ud5lUprHXQFgg`,
    },
  };
  const addTemplateData = useAuthLazyFetchDelete(
    `https://v1-orm-lib.mars.hipso.cc/notes/${id}`,
    deleteOptions
  );
  note.value.forEach((item: any, index: any) => {
    item.uid == id ? note.value.splice(index, 1) : "";
  });
}
</script>