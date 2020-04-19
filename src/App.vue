<template>
  <div id="app">
    <SamsungTV
      title="Samsung TV Control"
      description="Use these buttons to remote control the Samsung TV"
    />
  </div>
</template>

<script>
import SamsungTV from "./components/SamsungTV.vue";

export default {
  name: "App",
  components: {
    SamsungTV
  }
};
</script>

<style>
@font-face {
  font-family: Orbitron;
  src: url('./assets/fonts/Orbitron-Regular.ttf');
}

#app {
  background: #1c1c1c;
  padding: 100px;
  text-align: center;
  font-family: Orbitron;
}
</style>
