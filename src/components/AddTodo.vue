<template>
  <form @submit.prevent="onSubmit()">
    <input class="input-group-text" type="text" v-model="title">
    <button class="btn btn-dark" type="submit">Создать</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      console.log("Submit", this.title)
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>


<style scoped>
  form {
    display: flex;
    align-items: baseline;
  }

  input {
    width: 400px;
    margin-right: 10px;
    margin-bottom: 10px;
  }
</style>