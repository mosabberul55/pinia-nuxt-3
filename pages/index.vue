<template>
  <div class="main">
    <div class="header">
      <h1>To Do</h1>
      <p>completed: {{ todoStore.completed }}</p>
      <button class="btn" @click="addTodo">Add Todo</button>
    </div>
    <div class="section-main">
      <div class="todo-card" v-for="todo in todoStore.todos" :key="todo.id">
        <h3>{{ todo.title }}</h3>
        <div class="d-flex">
          <button class="btn btn-warning" @click="editData(todo)">Edit</button>
          <button class="btn btn-danger" @click="todoStore.deleteTodo(todo.id)">Remove</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useTodoStore} from "~/stores/todo";
const todoStore = useTodoStore()
const addTodo = () => {
  todoStore.addTodo({
    id: Math.floor(Math.random() * 1000),
    title: prompt('Todo title'),
    completed: false
  })
}
const editData = (todo) => {
  todoStore.editTodo({
    id: todo.id,
    title: prompt('Todo title'),
    complete: todo.complete
  })
}
</script>

<style scoped>
.main {
  padding: 20px;
}
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
.btn {
  font-size: 18px;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #0d4506;
  color: #fff;
  cursor: pointer;
}
.header h1 {
  font-size: 2rem;
  text-align: center;
}
.section-main {
  width: 70%;
  margin: auto;
  text-align: center;
}
.todo-card {
  padding: 5px;
  border: 1px solid #000;
  margin: 5px 0;
}
.btn-danger {
  font-size: 14px;
  background-color: #ab1414;
}
.btn-warning {
  font-size: 14px;
  background-color: #ab8f14;
}
.d-flex {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
</style>