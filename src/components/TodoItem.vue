<template>
  <li class="list-group-item">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed">
      <strong> {{index + 1}}. </strong>
      {{todo.title}}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)"></button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  }
}
</script>


<style scoped>
  li {
    border: 1px solid #ccc !important;
    display: flex;
    justify-content: space-between;
    padding: 20px 2rem;
    margin-bottom: 1rem;
    align-items: center;
  }

  .rm {
    position: relative;
    width: 30px;
    height: 30px;
    background-color: #ff4d4f; /* красный цвет */
    border: none;
    border-radius: 50%;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.2s;
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  }

  .rm::before,
  .rm::after {
    content: "";
    position: absolute;
    left: 50%;
    top: 50%;
    width: 20px;
    height: 2px;
    background-color: white;
    transform-origin: center;
  }

  .rm::before {
    transform: translate(-50%, -50%) rotate(45deg);
  }

  .rm::after {
    transform: translate(-50%, -50%) rotate(-45deg);
  }

  .rm:hover {
    background-color: #d9363e;
    transform: scale(1.1);
  }

  .done {
    text-decoration: line-through;
  }

  input {
    margin-right: 10px;
  }
</style>