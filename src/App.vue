<template>
  <div id="app">
    <!--Event Handling-->
    <app-counter initialValue="2"></app-counter>
    <app-counter></app-counter>
    <!--Each appcounter has it's own state so these will be indepentdent-->
    <app-counter></app-counter>
    <!-- use v-on to monitor dom for click and then update the value-->
    <app-counter2></app-counter2>
    <input type="text" v-on:keyup="number++">
    <!-- counts the number of vharacters entered-->
    {{ number}}
    <!--Event modifier-->
    <form v-on:submit.prevent="number++">
      <input type="text">
    </form>
    <!-- Key modifier-->
    <input type="text" v-on:keyup.enter="number++">
  </div>
</template>

<script>
import Vue from "vue";

export default {
  name: "App",
  data: function() {
    return {
      number: 0
    };
  }
};

Vue.component("app-counter", {
  props: ["initialValue"],
  data: function() {
    return {
      value: 0
    };
  },
  methods: {
    count: function(initialValue) {
      this.value += parseInt(initialValue);
      console.log(this.value);
    }
  },
  template: '<button v-on:click.once="count">{{ value }} </button>'
});
Vue.component("app-counter2", {
  data: function() {
    return {
      value: 0
    };
  },
  template: '<button v-on:mouseover="value++">{{ value }} </button>'
});
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
