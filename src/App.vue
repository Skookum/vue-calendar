<template>
  <div>
    <Title />
    <label><input
      v-model="todoItem"
      placeholder="Enter Todo Item..."><button @click="addTodo()">Add</button></label>
    <p v-if="todos.length">
      <ul
        v-for="todo in todos"
        :key="todo.id"
        style="padding: 0">
        <label><input
          :checked="todo.completed"
          type="checkbox"
          style="margin-right: 5px"
          @change="completeTodo(todo)">{{ todo.description }}</label>
      </ul>
    </p>
    <p v-else>
      There are no todo items yet
    </p>
  </div>
</template>

<script>
import Title from './Title.vue'
export default {
  components: {
    Title
  },
  data () {
    return {
      title: 'Simple Todo List',
      todoItem: '',
      todos: []
    }
  },
  methods: {
    addTodo: function () {
      this.todos.push({ description: this.todoItem, completed: false, id: this.todos.length })
      this.todoItem = ''
    },
    completeTodo: function (todo) {
      todo.isComplete = !todo.isComplete
    }
  }
}
</script>
