<template>
  <div id="app">
    <input v-model="message">
    <input :value="message" @input="handleChange">
    <div>
      <img alt="Vue logo" src="./assets/logo.png">
    </div>
    <span>{{message }} {{message + message}}</span>
    <div :id="message"></div>
    <todo-list>
      <todo-item @delete="handleDelete" v-for="item in list" :key="item.title" :title="item.title" :del="item.del">
        <template v-slot:pre-icon="{value}">
          <span>前置图标 {{value}}</span>
        </template>
      </todo-item>
    </todo-list>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'Todo-List',
  components: {
    TodoList,
    TodoItem
  },
  data() {
    return {
      message: "Hello-Vue.js",
      list: [
        {
          title: "课程 1",
          del: false
        },
        {
          title: "课程 2",
          del: true
        }
      ]
    }
  },
  methods: {
    handleChange(e) {
      this.message = e.target.value;
    },
    handleDelete(title) {
      console.log("handleDelete: ", title);
    }
  }
}
</script>

<style>
</style>
