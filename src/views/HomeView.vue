<template>

  <v-container>
    <v-card
    elevation="2"
    v-for = "(books, index) in book" :key = "books.id" 
    class="px-5 py-5 my-5">
  <router-link :to= "{ name: 'detalji', params: { bookID: index } }">  <v-btn class="mb-4">{{books.name}}</v-btn></router-link>
    <p>Prvi autor: {{books.authors[0]}}</p>
    <p>Datum izdavanja: {{books.released}}</p>
    </v-card>
  </v-container>

</template>

<script>
  import axios from 'axios'
  export default {
    name: 'Home',

    data(){
      return{
        book: "",
      }
    },
    methods:{
      async getRequest(){
       const dataBook = await axios.get(
        "https://www.anapioficeandfire.com/api/books"
      );
      this.book = dataBook.data;
      console.log(this.book)
    }
  },
  mounted(){
    this.getRequest();
  }
  }
</script>

<style scoped>
a{
  text-decoration: none;
}

</style>
