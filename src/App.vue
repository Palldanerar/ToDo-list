<template>
  <div class="header">
    <div class="container">
      <div class="logo">ToDo List</div>
      <div class="form">
        <input type="text" v-model="newTask" :placeholder="placeholder">
        <button class="btn" @click="ToDoAppend">Add in new task</button>
      </div>
    </div>
  </div>
  <app-to-do
  :todo="todo"
  @completeTask="completeTask"
  @removeTask="removeTask"
  ></app-to-do>
  <app-done
  :done="done"
  @returnTask="returnTask"
  @removeCompleteTask="removeCompleteTask"
  ></app-done>
</template>

<script>
import AppToDo from "@/components/AppToDo";
import AppDone from "@/components/AppDone"


export default {
  name: 'App',
  data() {
    return {
      todo: [],
      done: [],
      newTask: '',
      placeholder: "Записать новую задачу"
    }
  },
  methods: {
    ToDoAppend() {
      if (this.newTask.length !== 0) {
        this.todo.push(this.newTask)
        this.newTask = ''
      } else {
        this.placeholder = 'Вы ничего не ввели!'
      }
    },

    completeTask(index) {
      this.done.push(this.todo[index])
      this.todo.splice(this.todo[index], 1)
    },

    removeTask(index) {
      this.todo.splice(this.todo[index], 1)
    },

    returnTask(index) {
      this.todo.push(this.done[index])
      this.done.splice(this.done[index], 1)
    },

    removeCompleteTask(index) {
      this.done.splice(this.done[index])
    }
  },
  components: {
    AppDone,
    AppToDo
  }
}
</script>

<style scoped>


</style>
