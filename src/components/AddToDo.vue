<template>
  <div id="addATask">
    <input
      type="text"
      id="entry-field"
      v-model="title"
      v-on:keypress.enter="setMessage(title)"
    />
    <button id="add-butten" @click="setMessage(title)">Добавить</button>
    <button @click="findATask(title)" id="find-a-task">Найти</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    setMessage(value) {
      if (value != "") {
        const newToDo = {
          id: Date.now(),
          title: value,
          completed: false,
        };
        this.$emit("add-a-new-task", newToDo);
        this.title = "";
      }
    },
    findATask(value) {
      console.log(1);
      if (value != "") {
        this.$emit("find-a-task", value);
        this.title = "";
      }
    },
  },
};
</script>

<style>
#addATask {
  outline: none;
  width: 85%;
  height: 100%;
  font-size: 27px;
  border-radius: 3px;
}
#add-butten,
#find-a-task {
  width: 80px;
  height: 40px;
  border: none;
  background: #4c515b;
  color: #cfc2bd;
  font-size: 15px;
  cursor: pointer;
  border-radius: 5px;
  margin-left: 5px;
  margin-top: 5px;
}
#entry-field {
  width: 115%;
  height: 30px;
}
</style>