<template>
  <v-container>
    <v-card
    elevation="2"
    class="px-5 py-5"
    >
    <p>Prvi autor: {{book.authors[0]}}</p>
    <p>Datum izdavanja: {{book.released}}</p>
    <p>ISBN: {{book.isbn}}</p>
    <p>Broj stranica: {{book.numberOfPages}}</p>
    <p>Izdavac: {{book.publisher}}</p>
    <p>Zemlja podrijetla: {{book.country}}</p>
    <p>Broj likova: {{book.characters.length}}</p>
    <v-btn @click ="HomeFun">nazad</v-btn>
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
        ID: this.$route.params.bookID+1,
      }
    },
    methods:{
      async getRequest(){
       const dataBook = await axios.get(
        `https://www.anapioficeandfire.com/api/books/${this.ID}`
      );
      this.book = dataBook.data;
      console.log(this.book)
    },
    HomeFun(){
            this.$router.push('/')
        }
  },
  created(){
    this.getRequest();
  }
  }
</script>

<style>

</style>