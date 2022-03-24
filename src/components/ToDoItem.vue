<template>
  <li>
    <input type="checkbox" @change="$emit('do-check', task, 'need')" />
    {{ task.title }}
    <button id="delete-button" @click="$emit('delete-task', task.id,'need' )">X</button>
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