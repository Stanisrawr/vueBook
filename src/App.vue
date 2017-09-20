<template>
  <div id="app" class="container">

    <div class="page-header" id="head" style="text-align:center;">
      <img src="./assets/logo.png">
      <h1>Vue.JS & Firebase</h1>
    </div>
    <div class="panel panel-success">
      <div class="panel-heading">
        <h3>Add a book</h3>
      </div>
      <div class="panel-body">
        <form id="form" class="form-inline">
            <div class="form-group">
              <label for="bookTitle">Title:</label>
              <input type="text" id="bookTitle" value="">
              <label for="bookAuthor">Author:</label>
              <input type="text" id="bookAuthor" value="">
              <label for="bookURL">Url:</label>
              <input type="text" id="bookURL" value="">
            </div>
        </form>
      </div>

    </div>
    <br/>
    <div class="panel panel-primary">
      <div class="panel-heading">
        <h3>Books List</h3>
      </div>
      <div class="panel-body">
        <table class="table table-striped">
          <thead>
            <tr>
              <th>
                Title
              </th>
              <th>
                Author
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books">
              <td>
                <a v-bind:href="book.url">{{book.title}}</a>
              </td>
              <td>
                {{book.Author}}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import Firebase from 'firebase'
let config = {
  apiKey: "AIzaSyACr41QDTm6UlzuAgudtzwACzP9AfRkVHU",
  authDomain: "vuejstut.firebaseapp.com",
  databaseURL: "https://vuejstut.firebaseio.com",
  projectId: "vuejstut",
  storageBucket: "vuejstut.appspot.com",
  messagingSenderId: "728430037192"
}

let app = Firebase.initializeApp(config);
let db = app.database();
let booksRef = db.ref('books')

export default {
  name: 'app',
  firebase: {
    books: booksRef
  },
  data() {
    return {
      newBook: {
        title: '',
        Author: '',
        url: ''
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;


  color: #2c3e50;
  margin-top: 60px;
}
</style>
