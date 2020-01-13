<template>


<div>
 
  <b-card border-variant="dark" title="LIST" header-tag="header" footer-tag="footer">

    <b-card-text>     

<b-row >
    <b-col cols="4" >
 <form @submit.prevent="addTodo">
  
    <input v-model="newTodo" type="text" name="newTodo" id="newTodo" >
    <b-button type="submit" name="button" class="add">Add</b-button>
    
  </form>


    </b-col>
    <b-col cols="8" align-v="center">
      <ul >
    <li v-for="(todo, k) in todos" :key="k">
      <input type="checkbox" v-model="todo.done">
    <span :class="{done: todo.done}">{{todo.title}}</span>
    <b-button variant="outline-danger" @click="removeTodo(todo)" type="button" name="remove">Remove</b-button>
    </li>
  </ul>
</b-col>
  </b-row>
 

    </b-card-text>

<template v-slot:footer>
        
      </template>

       
  </b-card>
</div>




</template>







<script>
export default {
  data() {
    return {
    newTodo : '',
    todos: []
    }
  },
 

 methods: {
   addTodo() {
     this.todos.push({
       title: this.newTodo,
       finished: false
       
     });
     this.newTodo = '';
   },

   removeTodo(todo) {
     const todoIndex = this.todos.indexOf(todo);
     this.todos.splice(todoIndex, 1);
   },
 },
 
  mounted() {
    console.log('App mounted!');
    if (localStorage.getItem('todos')) this.todos = JSON.parse(localStorage.getItem('todos'));
  },
  watch: {
    todos: {
      handler() {
        console.log('Todos changed!');
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
   
 }

</script>

<style scoped>
.done {
  text-decoration: line-through;
}

ul {
  list-style-type: none;
 }

b-card {
  width : 100%;
}

</style>

