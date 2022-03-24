<template>
  <div id="app">
    <h1>Список задач</h1>
    <AddToDo @add-a-new-task="addANewTask" @find-a-task="findATask" />
    <h2 v-if="messageIndex === 0">Такая задача есть!</h2>
    <h2 v-else-if="messageIndex === 1">Такой задачи нет!</h2>
    <h2 v-if="arrayTasks.length < 1">Задач нет!</h2>
    <ToDoList
      v-else
      v-bind:arrayTasks="arrayTasks"
      v-bind:completedTasks="completedTasks"
      @delete-task="deleteTask"
      @reversed-items="reversedItems"
      @delete-all="deleteAll"
      @do-check="doCheck"
    />
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList";
import AddToDo from "./components/AddToDo";

export default {
  name: "App",
  data() {
    return {
      arrayTasks: [],
      completedTasks: [],
      messageIndex: -1,
    };
  },
  components: { ToDoList, AddToDo },
  methods: {
    deleteTask(id, type) {
      if (type === "need") {
        this.arrayTasks = this.arrayTasks.filter((t) => t.id != id);
      } else {
        this.completedTasks = this.completedTasks.filter((t) => t.id != id);
      }
    },
    addANewTask(todo) {
      this.arrayTasks.push(todo);
    },
    reversedItems() {
      return this.arrayTasks.reverse();
    },
    deleteAll() {
      this.arrayTasks = [];
      this.completedTasks = [];
    },
    doCheck(task, type) {
      if (type === "need") {
        const elem = {
          id: task.id,
          title: task.title,
          completed: true,
        };
        this.arrayTasks = this.arrayTasks.filter((t) => t.id != task.id);
        this.completedTasks.push(elem);
      } else {
        const elem = {
          id: task.id,
          title: task.title,
          completed: false,
        };
        this.completedTasks = this.completedTasks.filter(
          (t) => t.id != task.id
        );
        this.arrayTasks.push(elem);
      }
    },
    findATask(value) {
      console.log(value);
      if (this.arrayTasks.includes(value)) {
        this.messageIndex = 0;
        console.log(3);
      } else if (this.completedTasks.includes(value)) {
        this.messageIndex = 0;
        console.log(4);
      } else {
        this.messageIndex = 1;
        console.log(5);
      }
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