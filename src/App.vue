<template class="bg-gray--300">
<navbar/>
    <router-view />
</template>
<script>
import { defineComponent } from 'vue';
import Navbar from './components/Navbar.vue';

export default defineComponent({
  name: 'App',
  components:
  {
    Navbar,
  },
});
</script>

<style lang="css">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

#nav {
    padding: 30px;

    a {
        font-weight: bold;
        color: #2c3e50;

        &.router-link-exact-active {
            color: #42b983;
        }
    }
}
</style>
