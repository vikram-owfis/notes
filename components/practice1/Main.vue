<template>
  <div class="flex">
    <div :key="re_render">
      <practice1Add @inputData="inputData" />
      <practice1Edit @customPutemit="edited" :data="editcallDetails" />
    </div>
    <div>
      <practice1List
        class="mr-20 w-[30rem]"
        :details="details"
        @editdata="openEdit"
      />
    </div>
  </div>
</template>
<script setup>
const details = ref([]);
const is_edit = ref(false);
const re_render = ref(false);
const editcallDetails = ref({});
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

const openEdit = (data) => {
  console.log("data---------->", data);
  is_edit.value = true;
  re_render.value++;
  editcallDetails.value = data;
};

// const customPut = async (data) => {
//   const putOptions = {
//     method: "PUT",
//     headers: {
//       "Content-Type": "application/json",
//       Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
//     },
//     body: { data },
//   };
//   const putURL = await useAuthLazyFetchPut(
//     `https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,
//     putOptions
//   );
// };

async function edited(data) {
  console.log("data", data);
  const putOptions = {};
  await useAuthLazyFetchPut(
    `https://v1-orm-lib.mars.hipso.cc/api/pages/${data.uid}`,
    putOptions
  );
}
</script>


