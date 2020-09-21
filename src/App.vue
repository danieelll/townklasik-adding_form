<template>
  <div id="app" class="container">
    <b-row class="mb-3">
      <b-col md="3">
        <b-form-input v-model="filter" type="search" id="filterInput" placeholder="Type to Search"></b-form-input>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-table striped hover outlined :items="posts" :fields="fields" :filter="filter">
          <template v-slot:cell(actions)="data">
            <b-button variant="danger" @click="deleteItem(data.item.id)">Delete</b-button>
          </template>
        </b-table>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      fields: ["userId", "id", "title", "actions"],
      filter: "",
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
    };
  },
  methods: {
    deleteItem(id) {
      alert(`Sample delete of post with ID: ${id}`);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
