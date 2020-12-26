import { clearInterval } from 'timers';
import { clearInterval } from 'timers';
<template>
    <div>
        <div class="block" v-if="showBlock" @click="stopTimer">
            click me
        </div>
    </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
      showReactionTime: false
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {
    // console.log("component updated");
  },
  unmounted() {
    // console.log("component unmounted");
  },
  methods: {
    startTimer() {
      // start reactionTimer with setInterval
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
    //   console.log(this.reactionTime);
      this.$emit('endTimer', this.reactionTime)
    }
  }
};
</script>
    
<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
    

