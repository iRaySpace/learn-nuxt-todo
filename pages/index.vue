<template>
  <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
      <div class="mb-4">
        <h1 class="text-grey-darkest">Todo List</h1>
        <div class="flex mt-4">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
            placeholder="Add Todo" v-model="titleText">
          <button class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal"
            @click="addTodo">Add</button>
        </div>
      </div>
      <div>
        <div class="flex mb-4 items-center" v-for="todo in todos">
          <p class="w-full text-grey-darkest">{{ todo }}</p>
          <button class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red"
            @click="removeTodo(todo)">Remove</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
  data: () => {
    const titleText: string = ''
    const todos: string[] = []
    return { titleText, todos }
  },
  methods: {
    addTodo() {
      this.todos = [...this.todos, this.titleText]
      this.titleText = ''
    },
    removeTodo(todo: string) {
      this.todos = this.todos.filter((x) => x !== todo)
    },
  }
})
</script>
