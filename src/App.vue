<script setup>
  import { ref } from 'vue';
  import AppHeader from "./components/AppHeader.vue";

  // テキストと相互バインド
  const newTodo = ref("");
  // Todoの配列
  const todos = ref([]);

  const addTodo = () => {
    // todosにnewTodoをpushする
    todos.value.push(newTodo.value);
    newTodo.value="";
  }

// 削除ボタンクリック時の関数
const removeTodo = (index) => {
  // spliceによる削除
  // 第一引数：todos配列のindex番目の要素を指定
  // 第二引数：何個消すか
  todos.value.splice(index, 1);
}
</script>

<template>
  <AppHeader charColor="red">Todoアプリ</AppHeader>
  <input type="text" v-model="newTodo"> 
  <button @click="addTodo()">追加</button>

  <ul v-if="todos.length > 0">
    <li v-for="(todo, i) in todos" v-bind:key="i">{{ todo }} <button @click="removeTodo(i)">削除</button></li>
  </ul>
  <p v-else>Todoの追加をしてください</p>
</template>