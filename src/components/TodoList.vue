<template>
  <div>
    <ul class="list-group">
      <TodoItem v-for="(todo, i) of todos"
                v-bind:todo="todo"
                v-bind:index="i"
                v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'
export default {
  components: {
    TodoItem
  },
  props: ['todos'],
  methods: {
    removeTodo(id) {
      console.log(id)
      this.$emit('remove-todo', id)
    }
  }

}

</script>


<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>