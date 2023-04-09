<template>
  <div>
    <div>
      <Practise2Add @inputData="inputData" />
      <Practise2List :details="details" @edit="editData" />
      <Practise2Edit
        v-if="isEdit"
        :key="render"
        :updateData="updateData"
        @editData="editData"
      />
    </div>
  </div>
</template>
<script setup >
const details = ref("");
const open = ref("false");
async function inputData(input) {
  const postoptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
    body: {
      project_id: "string",
      name: input.name,
      subject: input.subject,
      body: input.body,
      is_active: "1",
      type: "HTML",
      share_type: "PRIVATE",
      category: input.category,
    },
  };

  const data = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/api/email-templates/",
    postoptions
  );
  details.value = data.data._rawValue;
}
const render = ref(0);
const isEdit = ref(false);
const updateData = ref({});
const editData = (data) => {
  isEdit.value = true;
  render.value++;
  updateData.value = data;
  const putoptions = {
    method: "PUT",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
    body: {
      name: data.name,
      category: data.category,
      body: data.body,
      subject: data.subject,
    },
  };
  const putData = useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/api/email-templates/${data.uid}`,
    putoptions
  );
};

const getData = useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/api/email-templates/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
details.value = getData.data._rawValue;
</script>