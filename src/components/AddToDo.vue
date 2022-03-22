<template>
  <div id="addATask">
    <input
      type="text"
      id="entry-field"
      v-model="title"
      v-on:keypress.enter="setMessage(title)"
    />
    <button id="add-butten" @click="setMessage(title)">Добавить</button>
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
#add-butten {
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