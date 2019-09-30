<template>
  <div>
    <h1>{{todos.length}}</h1>
    <table class="todoList">
      <tr class="todoList__title">
        <th v-on:click="$emit('handleSortBy', 'id')">#</th>
        <th v-on:click="$emit('handleSortBy', 'title')">Title</th>
        <th v-on:click="$emit('handleSortBy', '')">User</th>
        <th v-on:click="$emit('handleSortBy', 'completed')">Status</th>
      </tr>

      <TodoItem
        v-for="todo in todos" :key="todo.id"
        v-bind:todo="todo"
      />
    </table>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue';

export default {
  props: ['todos'],
  components: {
    TodoItem,
  },
};
</script>

<style scoped>
  .todoList {
    text-align: left;
    font-size: 20px;
    margin: 0 auto;
  }

  .todoList__title {
    font-weight: bold;
    font-size: 24px;
  }

  .todoList__title th, td {
  border-bottom: 1px solid rgb(99, 95, 95);
  }

  .todoList__title th:hover {
    cursor: pointer;
  }
</style>
