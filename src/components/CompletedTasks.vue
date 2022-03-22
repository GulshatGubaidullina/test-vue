<template>
  <li>
    <input type="checkbox" @change="$emit('do-check', task.id, 'completed')" />
    {{ task.title }}
    <button id="delete-button" @click="$emit('delete-task', task.id)">X</button>
  </li>
</template>

<script>
export default {
  props: ["task"],
};
</script>

<style>
li {
  padding: 1em;
  list-style-type: none;
}
#delete-button {
  border-radius: 30%;
}
</style>