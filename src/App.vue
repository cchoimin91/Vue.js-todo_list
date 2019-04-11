<template>
    <div id="app">
      <TodoHeader></TodoHeader>
      <TodoInput v-on:addTodo="addTodo"></TodoInput>
      <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
      <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
    </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue' // ES6 방식 
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data(){
      return {
        todoItems: []
      }
  },

  created() {
      if(localStorage.length>0){
        for(var i=0; i<localStorage.key(i); i++){
          this.todoItems.push(localStorage.key(i));
        }
      }
  },

  methods: {
      addTodo(todoItem){
        if(this.newTodoItem !==''){
          localStorage.setItem(todoItem, todoItem);
          this.todoItems.push(todoItem);
          alert('저장 성공');
        }
      },

      clearAll(){
        localStorage.clear();
        this.todoItems=[];
        alert('모두 삭제완료');
      },

      removeTodo(todoItem, index){
        localStorage.removeItem(todoItem);
        this.todoItems.splice(index,1);
        alert('['+todoItem+'] 삭제완료');
      }
  },

  components :{
                  'TodoHeader': TodoHeader,
                  'TodoInput': TodoInput,
                  'TodoList': TodoList,
                  'TodoFooter': TodoFooter
              }
}
</script>

<style>
   body{
     text-align: center;
     background-color: #F6F6F8
   }
   input {
     border-style: groove;
     width: 200px;
   }
   button{
     border-style: groove;
   }
   .shadow{
     box-shadow: 5px 10px 10px rgba(0,0,0, 0.03)
   }
</style>
