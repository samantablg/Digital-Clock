<template>
    <div class="html-clock">
        <div class="hours">{{ hours }}</div>
        <div class="sep">:</div>
        <div class="minutes">{{ minutes }}</div>
        <div class="sep">:</div>
        <div class="seconds">{{ seconds }}</div>
        <div class="mode">:</div>
    </div>
</template>

<style lang="postcss" scoped>
    .html-clock {
        display: grid;
        grid-template-columns: 3fr 1fr 3fr 1fr 3fr 1.5fr;
        justify-content: center;
        align-items: center;
        width: 500px;
        height: 125px;
    }

    .html-clock > div {
        display: flex;
        justify-content: center;
    }
    .sep { animation: blind 1s linear infinite; }

    @keyframes blink {
        0%,
        49% { opacity: 1; }

        50%,
        100% { opacity: 0; }
    }
    .red-lcd { color: red; }
    .green-lcd { color: green; }
    .yellow-lcd { color: yellow; }
</style>

<script>
export default {
   props: ['theme'],
   data: function () {
       return {
           hours: "--",
           minutes: "--",
           seconds: "--"
   }},
   methods: {
       updateTime() {
           this.hours = new Date().getHours();
           this.minutes = new Date().getMinutes();
           this.seconds = new Date().getSeconds();
       }
   },
   created () {setInterval(this.updateTime, 1000);},
   watch: {}
}
</script>
