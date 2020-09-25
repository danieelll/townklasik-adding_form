<template>
  <div>
    <BootstrapDatatable :posts="posts" />
    <VuetifyDatatable :posts="posts" />
  </div>
</template>

<script>
import BootstrapDatatable from "./components/BootstrapDatatable";
import VuetifyDatatable from "./components/VuetifyDatatable";

export default {
  name: "App",

  components: {
    BootstrapDatatable,
    VuetifyDatatable,
  },

  data: () => ({
    posts: [
      {
        userId: 1,
        id: 1,
        title:
          "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
      },
      {
        userId: 1,
        id: 2,
        title: "qui est esse",
      },
      {
        userId: 1,
        id: 3,
        title: "ea molestias quasi exercitationem repellat qui ipsa sit aut",
      },
    ],
  }),
};
</script>
