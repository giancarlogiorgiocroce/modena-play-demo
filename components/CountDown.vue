<template>
  <div class="ct center">
    <h1>mancano</h1>
    <div class="counter-ct">
      <div class="clock flex-c">
        <div class="num">{{ clocks.displayDays }}</div>
        <div class="time">giorni</div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ clocks.displayHours }}</div>
        <div class="time">ore</div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ clocks.displayMinutes }}</div>
        <div class="time">minuti</div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ clocks.displaySeconds }}</div>
        <div class="time">secondi</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
let clocks = {
  displayDays: ref(),
  displayHours: ref(),
  displayMinutes: ref(),
  displaySeconds: ref(),
}

const _seconds = computed(() => 1000);
const _minutes = computed(() => _seconds.value * 60);
const _hours = computed(() => _minutes.value * 60);
const _days = computed(() => _hours.value * 24);

const formatNum = (num:number) => {
  return num < 10 ? '0' + num : num;
}
const time = () => {  
  const timer = setInterval(() => {
    const now = new Date();
    const end = new Date(2023, 4, 19, 10, 10, 10, 10);
    const distance = end.getTime() - now.getTime();    

    if (distance < 0) {
      clearInterval(timer);
      return;
    }

    const days = Math.floor(distance / _days.value);
    const hours = Math.floor((distance % _days.value) / _hours.value);
    const minutes = Math.floor((distance % _hours.value) / _minutes.value);
    const seconds = Math.floor((distance % _minutes.value) / _seconds.value);

    clocks.displayDays.value = formatNum(days);
    clocks.displayHours.value = formatNum(hours);
    clocks.displayMinutes.value = formatNum(minutes);
    clocks.displaySeconds.value = formatNum(seconds);

  }, 1000)
}

time();
</script>

<style scoped lang="postcss">
.ct {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  margin: 5rem 0;

  text-transform: uppercase;
  color: #b0082b;
}

.counter-ct {
  display: flex;
  gap: 3rem;
}
.clock {
  height: 180px;
  width: 180px;
  padding: 7.5rem;

  font-weight: bolder;
  color: #b0082b;

  border: 10px solid rgba(240, 240, 240, 0.7);
  border-radius: 50%;
}

.num {
  font-size: 7rem;
}

.time {
  font-size: 20px;
  text-transform: uppercase;
}
</style>