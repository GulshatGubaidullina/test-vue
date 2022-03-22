<template>
  <div>
    <ul>
      <h2>Задачи</h2>
      <ToDoItem
        v-for="(task, index) in arrayTasks"
        :key="index"
        v-bind:task="task"
        @delete-task="deleteTask"
        @do-check="doCheck"
      />
    </ul>
    <ul>
      <h2>Выполненные задачи</h2>
      <CompletedTasks
        v-for="(task, index) in completedTasks"
        :key="index"
        v-bind:task="task"
        @delete-task="deleteTask"
        @do-check="doCheck"
      />
    </ul>
    <button @click="reversedItems" id="revers-btn">Сортировать</button>
    <button @click="deleteAll" id="delete-all-btn">Очистить</button>
  </div>
</template>
<script>
import ToDoItem from "@/components/ToDoItem";
import CompletedTasks from "@/components/CompletedTasks";

export default {
  props: ["arrayTasks", "completedTasks"],
  components: {
    ToDoItem,
    CompletedTasks,
  },
  methods: {
    deleteTask(id) {
      this.$emit("delete-task", id);
    },
    reversedItems() {
      this.$emit("reversed-items");
    },
    deleteAll() {
      this.$emit("delete-all");
    },
    doCheck(task, type) {
      this.$emit("do-check", task, type);
    },
  },
};
</script>

<style>
ul {
  padding-left: 0;
  list-style: none;
}
#revers-btn,
#delete-all-btn {
  width: 100px;
  height: 40px;
  border: none;
  outline: none;
  background: #4c515b;
  color: #cfc2bd;
  font-size: 15px;
  cursor: pointer;
  border-radius: 5px;
  margin-left: 5px;
  margin-top: 5px;
}
</style>