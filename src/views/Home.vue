<template>
  <div id="app" >
    <div class="todos-container"> 
      <Todos v-bind:todos="todos" v-on:del-tod="deleteTodo"/>
    </div>
    <AddTodo v-on:add-todo="addTodo"/>
  </div>
</template>

<script>
import AddTodo from '../components/AddTodo'
import Todos from '../components/todos'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: [
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todos = this.todos.filter(todo => todo.id != id))
      .catch(err => console.log(err));
     
    },
    addTodo(newTodo) {
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
      
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
    .then(res => this.todos = res.data)
    .catch(err => console.log(err));
  }
}
</script>

<style scooped>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  .todos-container{
    height: 560px;
    overflow-y: auto;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.5;
  }
  .btn{
    background: #333333;
    color: #ffffff;
    border: none;
  }
</style>
