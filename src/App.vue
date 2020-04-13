<template>
  <div id="app">
    <b-navbar type="dark" variant="dark" class="mb-4">
      <b-navbar-nav>
        <b-nav-item>
          <router-link to="/" class="white-text">Главная</router-link>
        </b-nav-item>
        <b-nav-item>
          <router-link to="/todos" class="white-text">Список дел</router-link>
        </b-nav-item>
      </b-navbar-nav>
    </b-navbar>
    <h1>Todo APP</h1>
    <hr />

    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.white-text {
  color: #fff;
  text-decoration: none;
}
.white-text:hover {
  color: #fff
}
</style>
