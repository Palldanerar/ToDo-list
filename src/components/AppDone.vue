<template>
  <div class="container">
    <h2>
      <span>Done List</span>
      <span class="mask-num">{{done.length}}</span>
    </h2>
    <ul class="mask-list complete-list" v-for="(made, index) in done" :key="made">
      <li>
        <div>
          <input type="checkbox" @change="$emit('returnTask', index)" checked>
          <span>{{made}}</span>
        </div>
        <button class="btn-remove" @click="$emit('removeCompleteTask', index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  emits: ['returnTask', 'removeCompleteTask'],
  name: "AppDone",
  props: ['done']
}
</script>

<style scoped>

</style>