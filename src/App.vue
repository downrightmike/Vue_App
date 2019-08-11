<template>
  <div id="app">
    <!--Event Handling-->
    <app-counter></app-counter>
    <app-counter></app-counter>
    <!--Each appcounter has it's own state so these will be indepentdent-->
    <app-counter></app-counter>
    <app-counter></app-counter>

    <!-- use v-on to monitor dom for click and then update the value-->
    <app-counter2></app-counter2>
    <input type="text" v-on:keyup="number++">
    <!-- counts the number of vharacters entered-->
    {{ number}}
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
  data: function() {
    return {
      value: 0
    };
  },
  template: '<button v-on:click="value++">{{ value }} </button>'
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
