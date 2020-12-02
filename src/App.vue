<template>
  <div id="app">
   <Header />
   <AddTodo v-on:add-todo="addTodo"/>
    <p v-if="load">loading...</p>
    <Todos v-else v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    

  </div>
</template>

<script>
import Header from './components/layout/header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTodo

  },
  data() {
    return{
      load:true,
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      
      axios.post(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(resp => this.todos = [...this.todos, resp.data])
      .catch(err => console.log(err));
    },
    addTodo(newTodo){
      
      axios.post('https://jsonplaceholder.typicode.com/todos', newTodo)
      .then(resp => this.todos = [...this.todos, resp.data])
      .catch(err => console.log(err));

    },
  },
      created(){
      // axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      // .then(res => this.todos = res.data)
      // .catch(err => console.log(err));
      

      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(resp => {
        this.load = false;
        (this.todos = resp.data);
          
      });
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
 
}
.btn {
  border: none;
  padding: 10px 20px;
  background-color: teal;
  color: white;
  font-weight: bold;
  cursor: pointer;
}
.btn:hover{
  background-color: rgb(2, 83, 83);
}
</style>
