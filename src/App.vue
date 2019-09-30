<template>
  <div id="app">
    <h1>Todo list</h1>
    <hr>
    <TodoList
      v-bind:todos="todos"
      v-on:handleSortBy="handleSortByKey"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue';
import getData from './api/getData';

export default {
  name: 'app',
  data() {
    return {
      todos: [],
      dir: 'asc',
    };
  },
  async mounted() {
    this.todos = await getData('https://jsonplaceholder.typicode.com');
  },
  methods: {
    handleSortByKey(key) {
      this.todos = this.todos.sort((a, b) => {
        if (key) {
          if (this.dir.localeCompare('asc')) {
            return (a[key] > b[key]) ? 1 : -1;
          }

          return (b[key] > a[key]) ? 1 : -1;
        }

        if (this.dir.localeCompare('asc')) {
          return (a.user.name.localeCompare(b.user.name));
        }

        return (b.user.name.localeCompare(a.user.name));
      });

      if (this.dir === 'asc') {
        this.dir = 'desc';
      } else if (this.dir === 'desc') {
        this.dir = 'asc';
      }
    },
  },
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
