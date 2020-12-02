<template>
  <div >
  <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
  </form>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: 'AddTodo',
  components: {

  },
  data() {
      return {
          title: ''
        
      }
  },
  methods: {
      addTodo(){

          //Send up to parent
          this.$emit('add-todo', {
              id:300,
              title: this.title,
              completed: false
          });

          this.title = '';
      }
  }

}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input[type=text] {
    padding: 10px;
    width:70%;
    box-sizing: border-box;
    border-radius: 0px;
    border:0px solid #ccc;
}
input[type=submit] {
    width: 30%;
}

</style>
