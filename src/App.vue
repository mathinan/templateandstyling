<template>
  <div id="app">
    <div class="nav-div">
      <router-link to="/" class="nav-link">Home</router-link>
      <router-link to="/viewbycolor" class="nav-link">View by color</router-link>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>

</style>