<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <input 
      v-model="todoTextInput"
      type="text"
      class="w-100 p-2"
      placeholder="Type Todo"
      @keyup.enter="addTodo"
    >
    <hr>
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleCheckBox"
    />
  </div>
</template>

<script>
import Todo from '@/components/Todo.vue';

export default {
  components: {
    Todo
  },
  data() {
    return {
      todoTextInput: '',
      todos: [
        { id: 1, text: 'buy a card', checked: false },
        { id: 2, text: 'play game', checked: false }
      ]
    }
  },
  methods: {
    addTodo(e) {
      
      this.todos.push({
        id: Math.random(),
        text: e.target.value,
        checked: false
      });

      this.todoTextInput = '';
    },
    toggleCheckBox({id, checked}) {
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });

      this.todos[index].checked = checked;
    }
  }

}
</script>

<style>
</style>
