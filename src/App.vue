<template>
  <div id="app">
    <h1>Список задач</h1>
    <AddToDo />
    <ToDoList v-bind:arrayTasks="arrayTasks" @delete-task="deleteTask" />
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList";
import AddToDo from "./components/AddToDo";

export default {
  name: "App",
  data() {
    return {
      arrayTasks: [
        {
          id: 1,
          title: "title1",
          completed: false,
        },
        {
          id: 2,
          title: "title2",
          completed: false,
        },
      ],
    };
  },
  components: { ToDoList, AddToDo },
  methods: {
    deleteTask(id) {
      this.arrayTasks = this.arrayTasks.filter((t) => t.id != id);
    },
  },
};
</script>

<style>
body {
  background-color: #f0f0f0;
  height: 100vh;
  width: 100%;
}
#app {
  margin: 120px auto;
  max-width: 400px;
  width: 100%;
  background: #918e94;
  border-radius: 5px;
  padding: 25px;
  color: #33353d;
  font-size: 18px;
}
#app h1 {
  font-size: 30px;
  font-weight: 600;
  text-align: center;
}
</style>