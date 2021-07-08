<template>
  <div id="root">
    <Header :addTodo='addTodo'/>
    <List :todos='todos' :deleteTodo='deleteTodo' :updateTodo='updateTodo'/>
    <Footer :todos='todos' :deleteAllSelected='deleteAllSelected'/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import List from './components/List.vue'
import Footer from './components/Footer.vue'

export default {
  data(){
    return {
      todos:[
        {content:'Going to get', done:true},
        {content:'Going to ahhhh', done:false}]
    }
  },
  components: {
    Footer, Header, List
  },methods:{
    deleteTodo(index){
      this.todos.splice(index, 1)
    },
    addTodo(todosObj){
      this.todos.unshift(todosObj)
    },
    updateTodo(index, e){
      this.todos[index].done = e.target.checked
    },
    deleteAllSelected(){
      this.todos = this.todos.filter((todoObj)=>{
        return !todoObj.done
      })
    }
  }, watch:{
      todos:{
        deep:true,
        handler(newValue){
          console.log(newValue)
        }
      }
    } 
  }
</script>

<style>
  #root{
    border: 1px solid red;
    width: 500px;
    margin: auto;
    padding: 10px;
  }
</style>
