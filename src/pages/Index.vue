<template>
  <div>
    <h1>Todoリスト</h1>
    <todo-form @handleParentAddTodo="handleParentAddTodo"></todo-form>
    <todo-list
     :todos="todos"
     @handleParentDeleteTodo="handleParentDeleteTodo"
     @handleParentCompleteTodo="handleParentCompleteTodo"></todo-list>
  </div>
</template>

<script>
import TodoForm from '../components/TodoForm.vue'
import TodoList from '../components/TodoList.vue'

  export default {
    name: 'Todo',
    components: {
      TodoForm,
      TodoList
    },
    data(){
      return{
        todos:[],
      }
    },
    methods:{
      handleParentAddTodo(value){
        if(value) {
          this.todos.unshift({text: value, complete: false});
        }
      },
      handleParentDeleteTodo(index){
        this.todos.splice(index,1);
      },
      handleParentCompleteTodo(index){
        this.todos[index].complete = !this.todos[index].complete
      }
    }
  }
</script>

<style scoped>

</style>