<template>
  <div class="hello">
    <Item v-for='(todos, index) in todos' 
    :todos='todos' 
    :index='index' 
    :deleteTodo='deleteTodo' 
    :updateTodo='updateTodo'/>
  </div>
</template>

<script>
import Item from './Item'
export default {
  data(){
    return {
      
    }
  },components:{
    Item,
  },props:['todos', 'deleteTodo','updateTodo'], 

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
