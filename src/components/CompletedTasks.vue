<template>
  <li id="completed-li">
    <input type="checkbox" @change="$emit('do-check', task, 'completed')" />
    {{ task.title }}
    <button
      id="delete-button"
      @click="$emit('delete-task', task.id, 'completed')"
    >
      X
    </button>
  </li>
</template>

<script>
export default {
  props: ["task"],
};
</script>

<style>
#completed-li {
  padding: 1em;
  list-style-type: none;
  opacity: 0.5;
}
#delete-button {
  border-radius: 30%;
}
</style>