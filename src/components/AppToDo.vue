<template>
  <div class="container">
    <h2>
      <span>ToDo List</span>
      <span class="mask-num">{{todo.length}}</span>
    </h2>
    <ul class="mask-list" v-for="(cases, index) in todo" :key="cases">
      <li>
        <div>
          <input type="checkbox" @change="$emit('completeTask', index)">
          <span>{{cases}}</span>
        </div>
        <button class="btn-remove" @click="$emit('removeTask', index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  emits: ['completeTask', 'removeTask'],
  name: "AppToDo",
  props: ['todo']
}
</script>

<style scoped>

</style>