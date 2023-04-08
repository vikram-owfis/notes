<template>
  <div class="flex justify-center">
    <practice1Add @inputData="inputData" />
    <practice1List class="mr-20" :details="details" @editdata="openEditModal" />
  </div>
</template>
<script setup>
const details = ref([]);

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
      page_html: null,
      page_css: null,
      is_published: true,
      last_published: null,
      meta_data: null,
      cdata1: null,
      cdata2: null,
    },
  };
  const data = await useAuthLazyFetchPost(
    "https://v1-orm-lib.mars.hipso.cc/api/pages/",
    postoptions
  );

  details.value = data.data._rawValue;
}
// get call
const getData = useAuthLazyFetch(
  "https://v1-orm-lib.mars.hipso.cc/api/pages/?offset=0&limit=100&sort_column=id&sort_direction=desc"
);
details.value = getData.data._rawValue;

// PUT call

const openEditModal = async (detail, index) => {
  console.log("detail,index", detail, index);
};
</script>


