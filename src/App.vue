<template>
  <div>
    <h2>simple output</h2>
    <div>
      <!-- Simple databinding, show the value of a variable, change value of variable -->
      {{ simpleOutputValue }}
    </div>
    <hr />
    <div>
      <!-- simple two way data binding with v-model -->
      <input v-model="inputValue" type="text" />
    </div>
    <!-- modifiers: v-model.modifier.modifier -->
    <div>
      <!-- -lazy - this waits for a loss of focus before updating. Performance increased! -->
      <!-- <input v-model.lazy="inputValue" type="text" /> -->
    </div>
    <div>
      <!-- .number - will ignore everything after it was last able to parse using parse.float -->
      <!-- <input v-model.number="inputValue" type="text" /> -->
    </div>
    <div>
      <!-- .trim - removes any spaces at the beginning and end of the string -->
      <!-- <input v-model.trim="inputValue" type="text" /> -->
    </div>
    <div>
      {{ inputValue }}
    </div>
    <div>
      <button v-on:click="updateText">Reset inputs</button>
    </div>
    <hr />
    <h2>direct variable manipulation without methods</h2>
    <div id="example-1">
      <button v-on:click="counter += 1">Add 1</button>
      <p>The button above has been clicked {{ counter }} times.</p>
      <button v-on:click="counter = 0">Reset</button>
    </div>
    <h2>v-on, @ and methods</h2>
    <div>show is: {{ show }}</div>
    <div>
      <button v-on:click="setShowTrue">Set show = true</button>
    </div>
    <div>
      <!-- theres a shorthand for v-on: it's called @ -->
      <button @click="setShowFalse">Set show = false</button>
    </div>
    <div>
      <button @click="toggleShow">Toggle show</button>
    </div>
    <hr>
    <h2>methods in inline handlers</h2>
    <div>
      <button @click="say('Hello, there!')">Say Hello</button>
    </div>
    <div>
      <button @click="say('What?')">Say What?</button>
    </div>
    <hr>
    <h2>v-if and v-else</h2>
    <!-- completely removes the element from DOM, can increase performance compared to v-show -->
    <div v-if="show">Show this IF show is TRUE</div>
    <div v-else>Show this IF show is FALSE</div>
    <hr>
    <h2>v-show</h2>
    <!-- Hides element in DOM using inline CSS, can increase performance compared to v-if -->
    <div v-show="show">Show this IF show is TRUE</div>
    <hr>
    <h2>v-for</h2>
    <ul id="array-rendering">
      <li v-for="(car, index) in cars" v-bind:key="car.id">
        {{ car.firstName }} {{ car.lastName }} - Index: {{ index }} - car.id: {{ car.id }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    simpleOutputValue: "Test",
    inputValue: "",
    show: false,
    counter: 0,
    message: "",
    cars: [
      {
        id: 1,
        firstName: "Sally",
        lastName: "Carrera",
      },
      {
        id: 2,
        firstName: "Lightning",
        lastName: "McQueen",
      },
      {
        id: 3,
        firstName: "Mater",
        lastName: "",
      },
    ],
  }),
  methods: {
    updateText() {
      this.inputValue = "Reset value";
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
    say(message) {
      alert(message);
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
  text-align: left;
  color: #2c3e50;
  margin-top: 40px;
}

div,
h2 {
  margin: 20px;
}
</style>
