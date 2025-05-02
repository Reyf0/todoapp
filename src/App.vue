<template>
  <header>
    <h1>TODO APP</h1>
  </header>
  <main>
    <AddTodo @add-todo="addTodo"/>
    <TodoList v-bind:todos="todos"
              @remove-todo="removeTodo"
    />
  </main>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodo from "@/components/AddTodo.vue";
export default {
  components: {
    TodoList, AddTodo
  },
  data() {
    return {
      todos: [
        {id: 1, title: "Купить хлеб", completed: false},
        {id: 2, title: "Купить молоко", completed: false},
        {id: 3, title: "Купить колбасу", completed: false}
      ]
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}

</script>


<style scoped>

</style>
