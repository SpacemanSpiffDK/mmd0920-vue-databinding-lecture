<template>
  <div id="app">
    <div>
      <input v-model="value" type="text" />
    </div>
    <!-- modifiers: v-model.modifier.modifier -->
    <div>
      <!-- <input v-model.lazy="value" type="text" /> -->
      <!-- this waits for a loss of focus before updating. Performance increased! -->
    </div>
    <div>
      <!-- <input v-model.number="value" type="text" /> -->
      <!-- will ignore everything after it was last able to parse using parse.float -->
    </div>
    <div>
      <!-- <input v-model.trim="value" type="text" /> -->
      <!-- removes any spaces at the beginning and end of the string -->
    </div>
    <div>
      {{ value }}
    </div>
    <div>
      <button @click="updateText">Reset inputs</button>
    </div>
    <div>
      <button @click="setShowTrue">Set show = true</button>
    </div>
    <div>
      <button @click="setShowFalse">Set show = false</button>
    </div>
    <div>
      <button @click="toggleShow">Toggle show</button>
    </div>

    <div>show is: {{ show }}</div>
    <div v-if="show">Show this IF show is TRUE</div>
    <div v-else>Show this IF show is FALSE</div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    value: "",
    show: false,
  }),
  methods: {
    updateText() {
      this.value = "Test";
    },
    setShowTrue() {
      this.show = true;
    },
    setShowFalse() {
      this.show = false;
    },
    toggleShow() {
      this.show = !this.show;
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-align: left;
}

div {
  margin: 20px;
}
</style>
