<template>
  <div id="app">
    <!-- Single component transition-->
    <button v-on:click="toggleShow">Toggle show</button>
    <transition name="myTransition">
      <!-- TRansition between more than one element, you need a unique key-->
      <!--<p v-if="show" key="my-transition-key">Hello transition</p>
      <p v-else kry="my-hello-key">Hello world</p>-->
      <app-home v-if="show" key="my-transition-key"></app-home>
      <app-about v-else kry="my-hello-key"></app-about>
    </transition>
    <br>
    <!-- Add an appear attributer to get the transitio on first view -->
    <transition appear name="myAnimation" enter="myClass">
      <p v-if="show">Hello animation</p>
    </transition>
  </div>
</template>

<script>
import Vue from "vue";
Vue.component("app-home", {
  template: "<div>Home</div>"
});
Vue.component("app-about", {
  template: "<div>About</div>"
});

export default {
  name: "App",
  data: function() {
    return {
      show: true
    };
  },
  methods: {
    toggleShow: function() {
      this.show = !this.show;
    }
  }
};
</script>

<style>
/*
v-enter v-enter-active v-enter-to v-leave v-leave-active v-leave-to
*/
.myTransition-enter-active,
.myTransition-leave-active {
  transition: opacity 0.5s;
}
.myTransition-enter-active,
.myTransition-leave-active {
  opacity: 0;
}
.myAnimation-enter-active {
  animation: bounce-in 0.5s;
}
.myAnimation-leave-active {
  animation: bounce-in 0.5s reverse;
}
.myClass {
  /* Super easy to make classes  to be able to combine a vue with a library like animate.css*/
}
/* Need to add a keygframe to control bounce*/
@keyfrane bounce-in {
  0% {
    transform: scale(0.5);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}
</style>
