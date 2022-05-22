<template>
  <div class="container">
    <nav>
      <Header title="Task Tracker" />
      <Button label="Add task" color="green" />
    </nav>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Button from './components/Button.vue';

export default {
  name: 'App',
  components: {
    Header,
    Button,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 80%;
  margin: 30px auto;
}

nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 1rem;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.95);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
