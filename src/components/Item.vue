<template>
  <div id='ItemRoot'
  @mouseenter='ItemStatus = true'
  @mouseleave='ItemStatus = false'
  :class="{'ItemStatus':ItemStatus}" >
    <label id='ItemDisplay'>
      <input type="checkbox" :checked='todos.done' @click='updateTodo(index,$event)'> 
      <p id='ItemContent'>{{todos.content}}</p>
    </label>
    <button id='ItemDelete' :style="{display:ItemStatus? 'block':'none'}" @click='doItemDelete'>Delete</button>
  </div>
</template>

<script>
export default {
  data(){
    return {
      ItemStatus: false,
    }
  },props:['todos','deleteTodo','index','updateTodo'],
  methods:{
    doItemDelete(){
      if(confirm('You sure to delete?')){
        this.deleteTodo(this.index)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #ItemRoot{
    border: 1px gray solid;
    display: flex;
    align-items: center;
  }
  #ItemDisplay{
    display: inherit;
    align-items: center;
    padding: 8px;
    width: 100%;
  }
  #ItemContent{
    margin: 5px;
    margin-left: 5px;
    flex-grow: 1;
  }
  .ItemStatus{
    background-color: green;
    transition: 0.3s;
  }
  #ItemDelete{
    background-color: red;
    color: white;
    height: 30px;
    cursor: pointer;
    margin-right: 5px;
  }

</style>
