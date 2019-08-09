<template>
  <div id="app">
    <app-header title="header title">
      <p>Some text</p>
    </app-header>
    <app-players v-bind:players="players"/>
    <local-component/>
  </div>
</template>

<script>
import Vue from "vue";

Vue.component("app-header", {
  props: ["title"],
  template: "<div>{{title}}: <slot></slot></div>"
});

Vue.component("app-players", {
  props: ["players"],
  template:
    "<div><ul><li v-for='player in players'><app-player v-bind:name='player.name'/></li></ul></div>"
});

Vue.component("app-player", {
  props: ["name"],
  template: "<div>{{name}}</div>"
});
var localComponent = {
  template: "<div>local component</div>"
};

export default {
  name: "App",
  data: function() {
    return {
      title: "some title",
      players: [{ name: "Bart" }, { name: "Joe" }]
    };
  },
  components: {
    "local-component": localComponent
  },
  //Life cycle hooks
  created: function() {
    console.log("created state");
  },
  mounted: function() {
    console.log("mounted state");
  }
};
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
