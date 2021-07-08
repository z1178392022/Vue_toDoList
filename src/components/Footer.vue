<template>
  <div id="FooterRoot">
    Select All <input type="checkbox" @click='checkedAll(todos, $event)' :checked=isAll>  |
    <p id="FooterLog">Compeleted: {{finished}}/All: {{allTodoItems}}</p>
    <button id="FooterButton" @click='deleteAllConfirm'>DeleteAllSelect</button>
  </div>
</template>

<script>
export default {
  data(){
    return {
    }
  },methods:{
    checkedAll(todos, e){
      if(e.target.checked === true){
        todos.map((todo)=>{
        todo.done = true;
       })
      }else{
        todos.map((todo)=>{
        todo.done = false;
       })
      }
    },
    deleteAllConfirm(){
      if(confirm('You sure to delete all seleted?')){
        this.deleteAllSelected()
      }
    }
  },props:['todos', 'deleteAllSelected'],
  computed:{
    finished(){
      return this.todos.reduce((pre,current)=>{
        return pre += current.done?1:0
      },0)
    },
    allTodoItems(){
      return this.todos.length
    },
    isAll(){
      return this.finished === this.allTodoItems && this.allTodoItems != 0
    }
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #FooterRoot{
    margin-top:5px;
    display:flex;
    width:100%;
    align-items: center;
  }
  #FooterLog{
    margin: 5px;
    flex-grow:1;
  }
  #FooterButton{
    background-color:red;
    color:white;
    border: 1px gray solid;
    cursor: pointer;
    padding: 5px;
  }
  
</style>
