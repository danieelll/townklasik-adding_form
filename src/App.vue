<template>
  <div id="app" class="container">
    <b-row class="mb-3">
      <b-col md="3">
        <b-form-input v-model="filter" type="search" id="filterInput" placeholder="Type to Search"></b-form-input>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-table
          striped
          hover
          outlined
          :per-page="perPage"
          :items="posts"
          :fields="fields"
          :filter="filter"
          :current-page="currentPage"
        >
          <template v-slot:cell(actions)="data">
            <b-button variant="danger" @click="deleteItem(data.item.id)">Delete</b-button>
          </template>
        </b-table>
        <b-pagination
          v-model="currentPage"
          :total-rows="rows"
          :per-page="perPage"
          aria-controls="my-table"
        ></b-pagination>
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
      perPage: 10,
      currentPage: 1,
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
      const index = this.posts.indexOf((x) => x.id === id);
      this.posts.splice(index, 1);
    },
  },
  computed: {
    rows() {
      return this.posts.length;
    },
  },
};
</script>
