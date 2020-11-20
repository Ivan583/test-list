<template>
  <li>
    <div class="container">
      <div>
        <div>
          <button class="start">Start</button>
          <button class="finish">Finish</button>
          <div class="box">
            <span class="index" :class="{work: inProgress(elem), done: isCompleted(elem)}">
              <strong>{{ index + 1 }}</strong>
            </span>
            <span :class="{work: inProgress(elem),  done: isCompleted(elem)}">{{ elem.title }}</span>
          </div>
        </div>

        <div>
          <span :class="{work: inProgress(elem),  done: isCompleted(elem)}">{{ elem.description }}</span>
        </div>
      </div>

      <div>
        <button class="edit">Edit</button>
        <button class="delete" @click="removeTask(elem.id, elem.stage)">Delete</button>
      </div>
    </div>
  </li>
</template>

<script>
import { bus } from "@/bus.js";
export default {
  props: {
    elem: {
      type: Object,
      required: true
    },
    index: Number
  },

  methods: {
    inProgress(myStage) {
      return myStage.stage === "in work";
    },
    isCompleted(myStage) {
      return myStage.stage === "completed";
    },

    removeTask(id, stage) {
      if (stage === "completed") bus.$emit("remove-task", id);
      else alert("Задача не выполнена!");
    }
  }
};
</script>

<style scoped>
div {
  display: flex;
}

.container {
  justify-content: space-between;
  padding: 0.5rem 2rem;
  margin-bottom: 1rem;
  border: 1px solid green;
}

.box {
  width: 570px;
}

button {
  margin-right: 1rem;
  font-weight: bold;
  color: #fff;
}

.start {
  background-color: green;
}

.finish {
  background-color: blue;
}

.edit {
  background-color: blueviolet;
  width: 55px;
}

.delete {
  background-color: red;
}

span {
  margin-right: 1.5rem;
  text-align: left;
}

.index {
  width: 35px;
  margin-right: 0.5rem;
}

.work {
  color: green;
}

.done {
  color: black;
  text-decoration: line-through;
}
</style>
