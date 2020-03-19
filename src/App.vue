<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    
  </div>
</template>

<script>
import Header from './components/layouts/Header.vue'
import Todos from './components/Todos.vue'
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: [
        {
          id:1,
          title:"Adopt and owl",
          completed:false
        },
        {
          id:2,
          title:"Shit",
          completed:true
        }
      ]
    }
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id!=id)
    },

    addTodo(newTodo){
      console.log(newTodo);
      this.todos = [...this.todos, newTodo];
    }
  }
}
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

.btn{
  display: inline-block;
  border:none;
  background:grey;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>
