<template>
  <div class="container">
    <Header />
  </div>
</template>

<script>
import Header from './components/Header'


export default {
  name: "App",
  components: {
    Header,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500&display=swap');
#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 3px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 4px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
</style>
