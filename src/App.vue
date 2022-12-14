<template>
  <Headercomp/>
  <router-view/>
  <FooterComp/>
</template>

<script>
import Headercomp from "@/components/HeaderComp";
import FooterComp from "@/components/FooterComp";

export default {
  name: "App",
  components: {FooterComp, Headercomp},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

button {
  margin-top: 30px;
  border-radius: 36px;
  background: #FEE996;
  border: 0;
  font-weight: 700;
  font-size: 0.8em;
  display: block;
  padding: 10px 16px;
  letter-spacing: 2px;
}

.container {
  display: flex;
  justify-content: center;
}
</style>
