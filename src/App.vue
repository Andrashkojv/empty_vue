<template>
  <div id="app">
      <profile :userLink="user"> </profile>
      <table v-if="user.username.length>0">
        <tr>
          <th> # </th>
          <th>Автор</th>
          <th>Назва</th>
          <th>Ціна</th>
        </tr>
        <tr v-for="(book, index) in books" v-bind:key="book.title">
            <td> {{index+1}}</td>
            <td> {{book.author}}</td>
            <td> {{book.title}}</td>
            <td> {{book.price}}</td>
            <td> <button v-on:click="deleteElement(index)">  Delete  </button></td>      
        </tr>
      </table>

      <label> Автор <input v-model="newBook.author"></label>
      <label> Назва <input v-model="newBook.title"></label>
      <label> Ціна <input v-model="newBook.price"></label>
      <button v-on:click="addElement(newBook)"> Додати книгу </button>
  </div>
</template>

<script>
import message from "./message.vue"
import profile from "./profile.vue"

export default {
  name: 'app',
  components:{
    message,
    profile
  },
  data() {
    return {
        user:{username:"", token:""},
        newBook:{author:"", title:"",price:0},
        books: [{autor:"Шевченко", title:"Кобзар",price:499.95},{author:"Кінг", title:"Воно",price:600.00}]
    }
  } ,
  methods:{/*
    alertElement: function(value){
      alert(value);
    },
    deleteElement: function(index){
      this.numbers.splice(index,1);
    },
    addElement:function(value){
      if (+value || value===0){
        this.numbers.push(value);
      } else{
        this.newNumber = "";
        alert("Ви ввели не число!");
      }
    }*/

    addElement:function(value){
      let copy = Object.assign({}, value);   
      this.books.push(copy);
    },

    deleteElement: function(index){
      this.books.splice(index,1);
    },
  } 
}
</script>

<style scoped>
  table td{
    border: 1px solid black;
    border-collapse: collapse;
    width: 100px;
  }
</style>