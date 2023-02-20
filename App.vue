<template>
  <div id="app">
    <header class="header">
      <sui-menu id="nav" secondary pointing>
      <sui-menu-item :active="$route.path == '/'" link name="Home">
        <router-link to="/">Home</router-link>
      </sui-menu-item>
      <sui-menu-item :active="$route.path.includes('topic')" name="Topics">
        <router-link to="/topics">Topics</router-link>
      </sui-menu-item>
    </sui-menu>
    </header>
    <div class="main error" v-if="error">
      <error-view></error-view>
    </div>
    <div class="main data" v-else>
      <router-view />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from 'vue-property-decorator';
import ErrorView from './components/ErrorView.vue';
import { Menu, MenuItem } from 'semantic-ui-vue';

@Component({
  components: {
    'error-view': ErrorView,
    'sui-menu': Menu,
    'sui-menu-item': MenuItem,
  },
})
export default class App extends Vue {
  get error() {
    return this.$store.state.config.error;
  }
}
</script>


<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  width: 100%;
  height: 100%;
  flex-flow: column;
}
.header {
  display: flex;
}
#nav {
  margin-left: -44px;
  display: flex;
  justify-items: center;
  flex-grow: 1;
  justify-content: center;
  margin-top: 0;
  .item {
    a {
      font-weight: bold;
      color: #2c3e50;
    }
    &.active {
      a {
        color: #4DBA87;
      }
      border-color: #4DBA87;
    }
  }
}
.main {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
}
.copyright {
  padding: 5px;
}
a {
  color: #4DBA87;
}
</style>
