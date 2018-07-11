<template>
  <div id="app">
      <header>
        <nav>
          <ul>
            <li class="nav-item">
              <router-link :to="{name: 'Home'}" exact class="nav-link">
                <img class="logo" src="./assets/build-a-bot-logo.png" />
                Build-a-Bot
              </router-link>
            </li>
            <li class="nav-item">
              <router-link :to="{name: 'Build'}" exact class="nav-link">
                Build
              </router-link>
            </li>
            <li class="nav-item cart">
              <router-link to="/cart" exact class="nav-link">
                Cart
              </router-link>
              <div class="cart-items">
                  {{ cart.length }}
              </div>
            </li>
          </ul>
        </nav>
      </header>
      <div class="container">
        <aside class="aside">
          <router-view name="sidebar"/>
        </aside>
        <main>
          <router-view/>
        </main>
      </div>
    </div>
</template>

<script>
import { mapState, mapGeters } from 'vuex';

export default {
  name: 'app',
  computed: {
    // same as below
    // ...mapState(
    //   {cart: state => state.robots.cart,}
    // ),
    cart() {
      return this.$store.state.robots.cart;
    },
  },
};
</script>

<style>
body {
  background: linear-gradient(to bottom, #555, #999);
  background-attachment: fixed;
}
</style>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
.container {
  display: flex;
  margin: 10px auto 0;
  justify-content: center;
  
}
.aside {
  padding: 30px;
  background-color: #aaa;
  width: 100px;
  min-height: 300px;
}
main {
  padding: 30px;
  background-color: #fff;
  width: 964px;
  min-height: 300px;
}
header {
  background-color: #999;
  width: 1184px;
  margin: 0 auto;
}
ul {
  padding: 3px;
  display: flex;
}
.nav-item {
  display: inline-block;
  padding: 5px 10px;
  font-size: 22px;
  border-right: 1px solid #bbb;
}
.logo {
  vertical-align: middle;
  height: 30px;
}
.nav-link {
  text-decoration: none;
  color: inherit;
}
.router-link-active {
  color: #fff;
}
.nav-item.cart {
  position: relative;
  margin-left: auto;
  border-right: none;
}
.cart-items {
  position: absolute;
  top: -5px;
  right: -9px;
  font-size: 16px;
  width: 20px;
  height: 20px;
  text-align: center;
  display: inline-block;
  border-radius: 100px;
  background-color: mediumseagreen;
}
</style>
