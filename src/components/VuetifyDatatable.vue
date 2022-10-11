
<template>
  <v-app>
    <v-main>
      <v-container>
        <h2>Table</h2>
        <v-row>
          
          <v-col md="3">
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-col>
          <button @click="showText = !showText" type="button" class="btn_answer btn-primary mt-5">Add Account</button>
        </v-row>
        <v-row>
          <v-col>
            <v-data-table
              :headers="headers"
              :items="posts"
              :items-per-page="5"
              :search="search"
              class="elevation-1"
            >
              <template v-slot:item.actions="{ item }">
              
                <div class="b">
                <b-button small @click="deleteItem(item)">Delete</b-button>
                </div>
              </template>
            </v-data-table>
          </v-col>
        </v-row>
      </v-container>
          <div class="frame_add" v-if="!showText">
          <form action="" @submit="InsertNewAccount" method="POST" enctype="multipart/form-data">
            <h6 class="mt-3 ml-3">Add Account</h6>
            
            <label class="mt-5 ml-3" for="fcode">Code:</label>
            <input class="ml-3" type="text" id="fcode" name="code" :v-bind="code" placeholder="Your code..">
            <label class="mt-3 ml-3" for="fname">Name:</label>
            <input class="ml-3" type="text" id="fname" name="firstname" :v-bind="name" placeholder="Your name..">
            <label class="mt-3 ml-3" for="balance">Normal Balance:</label>
            <select class="mt-3 ml-3" id="balance" :v-bind="balance" name="balance">
              <option value="australia">Debit</option>
              <option value="canada">Credit</option>
            </select>
            <div class="form-check mt-5 ml-5">
              <input class="form-check-input" type="checkbox" v-bind="isActive" id="flexCheckDefault">
              <label class="form-check-label" for="flexCheckDefault">
                Is Active
              </label>
            </div>
            <div class="form-check mt-3 ml-5">
              <input class="form-check-input" type="checkbox" v-bind="isCostSpreading" id="flexCheckDefault">
              <label class="form-check-label" for="flexCheckDefault">
                Is cost spreading
              </label>
            </div>

                      
          <input class="btn_submit mt-5" type="submit" value="Submit">
        </form>
      </div>
    </v-main>
  </v-app>

  
</template>

<script>
  import axios from 'axios';
  export default {
    props: ["posts"],

    data() {
          return{
            showText: true,
          search: "",
          headers: [
            { text: "Code", value: "userId" },
            { text: "Name", value: "id" },
            { text: "Normal Balance", value: "title" },
            { text: "Actions", value: "actions", sortable: false },
          ],
          code: '',
          name: '',
          balance: '',
          isActive: false,
          isCostSpreading: false,
        };
    },
    created(){
      this.GetAccounts();
    },
    methods: {
      deleteItem(item) {
        const index = this.posts.indexOf((x) => x.id === item.id);
        this.posts.splice(index, 1);
      },

      GetAccounts() {
        let url = 'http://accounting.townklasik.com/accounts';

        const config = {
          headers: {
            'Access-Control-Allow-Origin': '*'
          }
        };
        axios.get(url, config).then((response) => {
          console.log("Accounts: " + response.data);
        });
      },

      InsertNewAccount(e) {
        e.preventDefault;
        let url = 'http://accounting.townklasik.com/accounts';
        let data = {
          code: this.code,
          name: this.name,
          balance: this.balance,
          isActive: this.isActive,
          isCostSpreading: this.isCostSpreading,
        };

        axios.post(url,data).then((response) => {
          console.log.apply(response.data);
        })
        .catch(function (err) {
            console.log(err.response.data);
        });
      }
    },
  };
</script>