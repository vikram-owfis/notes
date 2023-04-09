<template>
  <div>
    <Practise2Add @inputData="inputData" />
    <Practise2List :details="details" @edit="editData" />
    <Practise2Edit :updateData="updateData" @editData="editData" />
  </div>
</template>
<script setup>
const details = ref("");
async function inputData(input) {
  const postoptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
    body: {
      name: input.name,
      category: input.category,
    },
  };
  const data = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/api/pages/",
    postoptions
  );
  details.value = data.data._rawValue;
}
const updateData = ref({});
const editData = (data) => {
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
    },
  };
  const putData = useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,
    putoptions
  );
};

const getData = useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/api/pages/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
details.value = getData.data._rawValue;
</script>