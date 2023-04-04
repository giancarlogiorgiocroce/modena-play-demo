<template>
  <div class="ct center">
    <h1>mancano</h1>

    <div class="counter-ct">
      <div class="clock flex-c">
        <div class="num">{{ displaySeconds }}</div>
        <div class="time">secondi</div>
        <div class="bar">
          <div class="progress" :style="{ width: progressPercentageSec }"></div>
        </div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ displayMinutes }}</div>
        <div class="time">minuti</div>
        <div class="bar">
          <div class="progress" :style="{ width: progressPercentageMin }"></div>
        </div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ displayHours }}</div>
        <div class="time">ore</div>
        <div class="bar">
          <div class="progress" :style="{ width: progressPercentageHours }"></div>
        </div>
      </div>
      <div class="clock flex-c">
        <div class="num">{{ displayDays }}</div>
        <div class="time">giorni</div>
        <div class="bar">
          <div class="progress" :style="{ width: progressPercentageDays }"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
let displayDays= ref();
let displayHours= ref();
let displayMinutes= ref();
let displaySeconds= ref();

const progressPercentageSec = computed(() => {
  const percentage = (displaySeconds.value * 100) / 60;
  return `${percentage}%`;
});
const progressPercentageMin = computed(() => {
  const percentage = (displayMinutes.value * 100) / 60;
  return `${percentage}%`;
});
const progressPercentageHours = computed(() => {
  const percentage = (displayHours.value * 100) / 24;
  return `${percentage}%`;
});
const progressPercentageDays = computed(() => {
  const percentage = (displayDays.value * 100) / 60;
  return `${percentage}%`;
});

const _seconds = computed(() => 1000);
const _minutes = computed(() => _seconds.value * 60);
const _hours = computed(() => _minutes.value * 60);
const _days = computed(() => _hours.value * 24);

const time = () => {  
  const timer = setInterval(() => {
    const now = new Date();
    const end = new Date(2023, 4, 19, 10, 10, 10, 10);
    const distance = end.getTime() - now.getTime();    

    if (distance < 0) {
      clearInterval(timer);
      return;
    }

    displayDays.value = Math.floor(distance / _days.value);
    displayHours.value = Math.floor((distance % _days.value) / _hours.value);
    displayMinutes.value = Math.floor((distance % _hours.value) / _minutes.value);
    displaySeconds.value = Math.floor((distance % _minutes.value) / _seconds.value);

  }, 1000)
}

time();
</script>

<style scoped lang="postcss">
.ct {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 5rem auto;
}

h1 {
  font-size: 3rem;
  text-transform: uppercase;
  color: #b0082b;
}

.counter-ct {
  margin: 3rem 0;
  display: flex;
  gap: 3rem;
}
.clock {
  height: 180px;
  width: 180px;
  padding: 6rem;

  font-weight: bolder;
  color: #b0082b;

  border: 10px solid rgba(240, 240, 240, 0.7);
  border-radius: 50%;
}

.num {
  font-size: 5rem;
}

.time {
  font-size: 20px;
  text-transform: uppercase;
}

.bar {
  margin: 1rem 0.5rem;
  min-width: 15vw;
  background: #b0082b;
  transform: rotate(180deg);
  border: 2px dashed white;
}

.progress {
  min-height: 10px;
  max-width: 90vw;
  background: rgba(240, 240, 240);
}

@media only screen and (max-width:980px) {

  h1 {
    font-size: 1.7rem;
  }

  .counter-ct {
    flex-wrap: wrap;
    justify-content: space-around;
  }
  .clock {
    height: 120px;
    width: 120px;
    padding: 5rem;
  }

  .num {
    font-size: 3.5rem;
  }

  .time {
    font-size: 16px;
  }
}
</style>