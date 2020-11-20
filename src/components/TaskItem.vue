<template>
  <li>
    <div class="container">
      <div>
        <div>
          <button class="start">Start</button>
          <button class="finish">Finish</button>
          <div class="box">
            <span class="index" :class="{work: inProgress(elem)}">
              <strong>{{ elem.id }}</strong>
            </span>
            <span :class="{work: inProgress(elem)}">{{ elem.title }}</span>
          </div>
        </div>

        <div>
          <span :class="{work: inProgress(elem)}">{{ elem.description }}</span>
        </div>
      </div>

      <div>
        <button class="edit">Edit</button>
        <button class="delete">Delete</button>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    elem: {
      type: Object,
      required: true
    }
  },

  methods: {
    inProgress(myStage) {
      return myStage.stage === "in work";
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
  margin-right: 0.5rem;
}

.work {
  color: green;
}
</style>
