<script setup lang="ts">
import { ref } from 'vue';
import type { Todo } from './types/Todo';

// État de la liste de tâches et de la nouvelle tâche
const todos = ref<Todo[]>([
  { id: 1, content: 'Courses Lidl', done: false },
  { id: 2, content: 'Devis garage', done: true },
  { id: 3, content: 'Courses Leroy-Merlin', done: false },
]);

const newTodoText = ref('');

const addTodo = () => {
};

const toggleTodo = (id: number) => {
};

const removeTodo = (id: number) => {
};
</script>

<template>
  <div class="container mt-5">
    <div class="card shadow-lg p-4">
      <h1 class="text-center mb-4">À faire cette semaine</h1>

      <div class="input-group mb-4">
        <input
          type="text"
          class="form-control"
          placeholder="Nouvelle tâche..."
          v-model.trim="newTodoText"
          @keyup.enter="addTodo"
        />
        <button class="btn btn-primary" @click="addTodo" :disabled="!newTodoText">
          Ajouter
        </button>
      </div>

      <ul class="list-group">
        <li v-if="todos.length === 0" class="list-group-item text-center text-muted">
          Toutes les tâches sont terminées yay \o/
        </li>
        <li
          v-for="todo in todos"
          :key="todo.id"
          class="list-group-item d-flex justify-content-between align-items-center"
          :class="{ 'list-group-item-success': todo.done }"
        >
          <span
            :class="{ 'text-decoration-line-through': todo.done, 'cursor-pointer': true }"
            @click="toggleTodo(todo.id)"
          >
            {{ todo.content }}
          </span>
          <button class="btn btn-sm btn-danger" @click="removeTodo(todo.id)">
            Supprimer
          </button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.cursor-pointer {
  cursor: pointer;
}
</style>