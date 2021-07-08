<template>
  <div id='HeaderRoot'>
    <input type="text" id='HeaderInput' @keyup.enter='doItemAdd'>
  </div>
</template>

<script>
export default {
  data(){
    return {
      
    }
  },props:['addTodo'],
  compeleted:{
    
  },
  methods:{
    doItemAdd(e){
      const obj = {content:e.target.value, done:false}
      this.addTodo(obj);
      e.target.value='';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #HeaderRoot{
    margin: auto;
    text-align: center;
  }
  #HeaderInput{
    width: 490px;
    height: 30px;
    font-size: 20px;
    margin-bottom: 10px
  }
</style>
