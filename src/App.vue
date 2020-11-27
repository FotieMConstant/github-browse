<template>
  <div id="app">
    <div id="nav"><Appbar /></div>
    <router-view />
  </div>
</template>

<script>
import Appbar from "@/components/Appbar.vue";

export default {
  components: {
    Appbar,
  },
};
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  margin-top: 100px;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
