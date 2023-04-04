<template>
  <div class="ct">
    <h1>Programma</h1>
    <div class="wrapper center">
      
      <div v-for="(card, i) in cardData" :key="i" class="card">
        <div class="text-ct">
          <h2>{{ card.title }}</h2>
          <div class="separator"></div>
          <p>{{ card.where }}</p>
          <p>{{ card.when }}</p>
        </div>
        <div class="img-ct">
          <img :src="card.image" alt="picsum">
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const cardData = [
  {
    title: "Armi & Armature: tre falsi miti di D&D",
    where: "Primo Piano - Sala 40",
    when: "Sabato 20 / ore 16:00",
    image: "https://picsum.photos/380/260"
  },
  {
    title: "Dungeons & Deejay, la rivelazione",
    where: "Galleria - 6 - 7",
    when: "Sabato 20 / ore 13:00",
    image: "https://picsum.photos/380/260"
  },
]

</script>

<style scoped lang="postcss">
.ct {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 5rem 0 7rem 0;
  background: lightgrey;
}

h1 {
  font-size: 3rem;
  text-transform: uppercase;
  color: #b0082b;
}

.wrapper {
  display: flex;
  gap: 2rem;

}

.card {
  background: white;
  border-radius: 20px;
  max-width: 390px;
  border: 5px solid #b0082b;
}

.card:hover {
  transform: rotateY(180deg);
}
.card:first-of-type {
  border: 5px solid grey;
}

.text-ct {
  padding: 30px;
}

h2 {
  font-size: 2rem;
}

.separator {
  height: 2px;
  margin-bottom: 1rem;
  background: #b0082b;
}

.card:first-of-type .separator {
  background: grey;
}

p {
  color: grey;
}

.img-ct {
  position: relative;
  bottom: -5px;

  width: 100%;
}

img {
  border-bottom-right-radius: 15px;
  border-bottom-left-radius: 15px;
  width: 100%;
  height: 100%;
}

@media only screen and (max-width:980px) {

  h1 {
    font-size: 1.7rem;
  }
}
</style>