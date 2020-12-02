<template>
  <div class="">
      <div class="todoitem" v-bind:class="{'is-complete' : todo.completed}">  
        <p>
            <input type="checkbox" v-model="checked" v-on:change="markComplete">
           
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
            </p>
    
      </div>
    
  </div>
</template>

<script>
export default {
  name: 'todoItem',
  props: ['todo'],
  data() {
      return{
          checked: false
      }
  },
  methods: {
      markComplete() {
          this.todo.completed = !this.todo.completed;

      }
  },
  created() {
      this.checked = this.todo.completed == true ?   true : false;
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todoitem {
    display: block;
    background-color: rgb(224, 224, 224);
    
    
}
.todoitem p{
    margin: 0px;
    padding: 10px;
    border-bottom:1px solid rgb(155, 155, 155) ;
}
.is-complete {
    text-decoration: line-through;
     /* background-color: rgb(112, 199, 156); */
}
button.del {
    float: right;
    background-color: rgb(206, 68, 68);
    width: 25px;
    height: 25px;
    text-align: center;
    border-radius: 50px;
    color: white;
    cursor: pointer;
    border: none;
}
button.del:hover {
    background-color: rgb(139, 40, 40);
}
</style>
