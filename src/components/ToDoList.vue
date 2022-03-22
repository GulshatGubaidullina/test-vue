<template>
  <div>
    <ul>
      <ToDoItem
        v-for="(task, index) in arrayTasks"
        :key="index"
        v-bind:task="task"
        @delete-task="deleteTask"
      />
    </ul>
  </div>
</template>
<script>
import ToDoItem from "@/components/ToDoItem";
export default {
  props: ["arrayTasks"],
  components: {
    ToDoItem,
  },
  methods: {
    deleteTask(id) {
      this.$emit("delete-task", id);
      console.log(id);
    },
  },
};
</script>

<style>
ul {
  padding-left: 0;
  list-style: none;
}
</style>