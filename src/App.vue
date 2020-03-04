<template>
  <div id="app" class="container">
    <Header />
    <router-view/>
  </div>
</template>
<script>
import Header from "./components/Header";
export default {
  name: "app",
  components: {
    Header
  }
}
</script>


<style>
.container {
  margin: 20px 33% 0 33%;
  border-radius: 10px;
  height: 700px;
  border: 2px solid #000000;
  overflow: hidden;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
