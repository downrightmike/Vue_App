<template>
  <div id="app">
    {{hello}}
    <!--text interpolation, will be replaced with data function-->
    <!-- If we want to have it update onnly once on load: we can use a directive via class-->
    <span v-once>{{hello}}</span>
    <!-- -->
    <span v-bind:id="myId" v-once>{{hello}}</span>
    
    <button v-bind-disabled="false">button disabled</button>
    <button v-bind-disabled="true">button disabled</button>
    
    <span>{{number + 2}}</span>
    <p v-if="userExist">USer Exists</p>
    <p v-else-if="number == 2">USer not Exists</p>
    <p v-else>USer not Exists</p>

    <a v-bind:href="href">link</a>
    <a :href="href">Short form directive</a>

    <form v-on:Submit.prevent="onSubmit">This is a form</form>

    <div v-on:click="onClickMethod">click</div>
    <div @click="onClickMethod">short syntax click</div>
    <!-- v-for is not iterating, checked docs, this is 2.x style -->
    <!-- UPdate: The sandbox needed to be reloaded. All v-fors work as expected-->
    <div v-for="(item, index) in items">
      <div v-if="index == persons.length -1">{{persons.name}}, {{index}}</div>
    </div>
    <div v-for="(item, index) in items">
      <div v-if="index == items.length - 1">yes</div>
      {{ item }}, {{ index }}
    </div>
    <!-- Look up for loops in Vue Docs because this isn't working as expected-->
    <div v-for="prop in player">
      <div>{{ prop}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      href: "www.example.com",
      userExist: true,
      number: 1,
      myId: "id2",
      hello: "hellol",
      persons: [{ name: "Bart" }, { name: "Joe" }],
      items: [{ item: "apple" }],
      player: {
        name: "Bart",
        age: 27,
        hobby: "art"
      }
    };
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
