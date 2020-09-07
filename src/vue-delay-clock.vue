<template>
  <p
    class="time"
    v-text="currentTime"
  ></p>
</template>

<script>
import moment from 'moment'

export default {
    name: 'VueDelayClock',
    props: {
        // 延迟展示时间，默认为0，比如延时5s展示，
        delay: {
            type: Number,
            default: 0
        }
    },
    data () {
        return {
            currentTime: null
        }
    },
    methods: {
        updateCurrentTime () {
            this.currentTime = moment().add(this.delay, 's').format('HH:mm:ss');
        }
    },
    created () {
        this.currentTime = moment().add(this.delay, 's').format('HH:mm:ss');
        setInterval(() => this.updateCurrentTime(), 1 * 1000);
    }
}
</script>

<style>
</style>
