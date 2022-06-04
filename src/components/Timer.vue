<template>
  <div class="container">
    <div class="timer">
      <span class="minutes">{{ minutes }}</span>
      <span>:</span>
      <span class="seconds">{{ seconds }}</span>
    </div>
    <div class="controls">
      <button @click="startTimer">
        <span class="material-icons play"> play_arrow </span>
      </button>
      <button @click="pauseTimer">
        <span class="material-icons pause"> pause </span>
      </button>
      <button @click="restartTimer">
        <span class="material-icons refresh"> refresh </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      remainingSeconds: 1500,
      minutes: "25",
      seconds: "00",
      interval: null,
    };
  },
  methods: {
    startTimer() {
      this.interval = setInterval(() => {
        this.remainingSeconds = this.remainingSeconds - 1;
        this.minutes = Math.floor(this.remainingSeconds / 60)
          .toString()
          .padStart(2, "0");
        this.seconds = (this.remainingSeconds % 60).toString().padStart(2, "0");

        if (this.remainingSeconds === 0) {
          this.pauseTimer();
        }
      }, 1000);
    },

    pauseTimer() {
      clearInterval(this.interval);
    },

    restartTimer() {
      this.remainingSeconds = 1500;
      this.minutes = "25";
      this.seconds = "00";
      this.pauseTimer();
    },
  },
};
</script>

<style>
.container {
  border: 1px solid rgb(41, 41, 41);
  border-radius: 16px;
  max-width: 300px;
  margin: 0 auto 40px;
  padding: 5px;
  background: rgb(41, 41, 41);
}

.timer {
  text-align: center;
  padding: 16px;
  font-size: 38px;
  font-weight: 700;
  color: white;
}

.controls {
  padding: 16px;
  text-align: center;
}

.controls button {
  background: transparent;
  border-radius: 100%;
  border: 2px solid white;
  height: 40px;
  width: 40px;
  align-content: center;
  margin: 0 5px;
}

.play,
.pause,
.refresh {
  color: white;
  cursor: pointer;
}
</style>