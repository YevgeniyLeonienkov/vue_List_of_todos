<template>
  <tr class="todoItem">
    <td>{{ todo.id }}</td>
    <td v-bind:class="{done: todo.completed}">{{ todo.title }}</td>
    <td>{{ todo.user.name }}</td>
    <td>
      <label for="completed">
        <input
          id="completed"
          type="checkbox"
          v-model="todo.completed"
        />
      </label>
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
  .todoItem:hover {
    background-color: beige;
  }

  .done {
    text-decoration: line-through;
  }
</style>
