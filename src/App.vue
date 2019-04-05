<template>
  <div id="app">
    <demo/>
  </div>
</template>

<script>
import demo from './views/demo'
export default {
  name: "app",
  components: {demo}
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
body,
#app {
  padding: 20px;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  background: rgba(243, 240, 240, 0.541);
}
</style>
