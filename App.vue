<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems"></TodoList>
    <TodoFooter  v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
// app.vue 에다가 4개의 컴포넌트를 불러와야 함.
// 모던 자바스크립트에서는 외부 파일을 불러오는 선언문 - import
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';
export default {
  data(){
    return {
      todoItems: []
    }
  },
  created(){
        // 만약에 로컬 스토리지의 갯수가 0보다 크다면
        // for문을 사용해서 배열형 변수 todoItems에 데이터를 담아야 함.
        if(localStorage.length > 0){
            for(var i=0; i < localStorage.length; i++){
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
  methods: {
    addTodo(todoItem){
      // 로컬스토리지에 데이터를 추가하는 로직을 구현
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;500;700&display=swap');
  body {
    font-family: 'ubuntu', sans-serif;
    text-align: center;
    background-color: #f6f6f8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
  }
</style>
