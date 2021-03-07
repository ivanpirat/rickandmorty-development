<template>
  <div class="help">
    <h1>справочник по Rick и Morty</h1>
    <img class="helpimg" src="./assets/3689114-1133880.jpg" alt="" />
  </div>
  <div class="HelloWorld">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
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
}
.HelloWorld {
  margin: 100px 3%;
  box-shadow: rgba(0, 0, 0, 0.39) 0 0 22px;
  padding: 5px;
  border-radius: 15px;
}
.helpimg {
  width: 100%;
  width: 100%;
  top: 0;

  left: 0;
}
.help {
  height: 100px;
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  overflow: hidden;
  box-shadow: black 0 0 13px;
}
.help h1 {
  position: fixed;
  left: 50%;
  color: white;
  transform: translate(-50%, 0);
  text-shadow: black 0 0 4px;
}
@media screen and (max-width: 800px) {
  .help {
    height: 200px;
  }
  .HelloWorld {
    margin-top: 210px;
  }
}
</style>
