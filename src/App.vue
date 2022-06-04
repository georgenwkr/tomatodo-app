<template>
  <header>
    <h1>tomatodo</h1>
    <p>
      'pomodoro' meaning tomato, + todo &#129325; . the pomodoro technique is a
      time management system that uses a timer to break work into intervals, 25
      minutes in length, separated by short breaks.
      <a href="https://en.wikipedia.org/wiki/Pomodoro_Technique" target="blank"
        >read more</a
      >. make a todo list and start the timer!
    </p>
  </header>
  <Timer />
  <Todos />
</template>

<script>
import Todos from "./components/Todos.vue";
import Timer from "./components/Timer.vue";

export default {
  name: "App",
  components: { Todos, Timer },
};
</script>

<style>
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: rgb(41, 41, 41);
  border-radius: 10px;
}

* {
  font-family: "Inter", sans-serif;
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h1 {
  font-size: 36px;
  color: #121212;
  font-weight: 800;
  text-align: center;
}

p {
  font-size: 16px;
  font-weight: 400;
  text-align: center;
  width: min(90%, 650px);
  margin: 20px auto;
  line-height: 1.4;
}
</style>
