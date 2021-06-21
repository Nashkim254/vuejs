<template>
   <div class="container">
       <div class="row">
           <div class="col-12">
               <p class="display-3"> Hello welcome to vue js</p>
           </div>
       </div>
       <div class="row">
           <p>Create Todo</p>
       </div>
       <div class="row">
           <div class="col-12 col-lg-6">
               <ul class="list-group">
                   <Todo v-for="(todo, index) in todos" :key ="index"
                   :todoString = "todo.todoString"
                   :completed = "todo.completed"
                   />
               </ul>
           </div>
       </div>
   </div>
</template>

<script>
import Todo from "./todo.vue"
export default {
    components:{
        Todo
    },
    data(){
        return { 
            todos:[
            {
                todoString: "Learn Vue Js", completed : false
            },
            {
                todoString: "Learn Laravel ", completed : true
            },
            {
                todoString: "Learn React Js", completed : false
            },
            {
                todoString: "Learn Fluter ", completed : true
            }
        ]
        }
    },
methods: {
    addTodo(newTodo){
        this.todos.push({
            todoString: newTodo,
            completed:false
        })
    },
    togleTodo(todo){
        todo.completed = !todo.completed;
    },
    editTodo(todo,newTodoString){
        todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo){
        this.todos = this.todos.filter(
            todo => todo.todoString !== deleteTodo.todoString
        );
    }
}
}
</script>

<style>

</style>