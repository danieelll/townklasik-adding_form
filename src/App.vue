<template>
  <div>
 
    <VuetifyDatatable :posts="posts" />
    
    
    
   
  </div>

 
</template>

<script>

import VuetifyDatatable from "./components/VuetifyDatatable";

export default {
  name: "App",

  components: {
 
    VuetifyDatatable,
  },

  data: () => ({
    
    posts: [
      {
        userId: 1,
        id: "Mark",
        title:
          "Debit",
      },
      {
        userId: 2,
        id: "Adrian",
        title: "Debit",
      },
      {
        userId: 3,
        id: "Daniel",
        title: "Credit",
        
      },
            {
        userId: 4,
        id: "Kyle",
        title: "Debit",
        
      },
      {
        userId: 5,
        id: "john",
        title: "Credit",
        
      },
      
    ],
  }),
};
</script>
