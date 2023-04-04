<template>
  <div class="ct">
    <h1>Programma</h1>
    <div class="wrapper center">

      <div v-for="(card, i) in cardData" :key="i" class="flip-card">
        <div class="flip-card-inner">

          <div class="flip-card-front">
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

          <div class="flip-card-back">
            <div class="text-ct">
              <h2>{{ card.title }}</h2>
              <div class="desc">
                {{ card.desc }}
              </div>
              <div class="separator"></div>
              <p>{{ card.where }}</p>
              <p>{{ card.when }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// DATA
const cardData = [
  {
    title: "Armi & Armature: tre falsi miti di D&D",
    where: "Primo Piano - Sala 40",
    when: "Sabato 20 / ore 16:00",
    image: "https://picsum.photos/380/260",
    desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium numquam temporibus dignissimos consectetur earum aliquam esse id pariatur, reprehenderit laboriosam sequi vitae veritatis labore magni? Porro reiciendis et, distinctio similique sapiente autem?"
  },
  {
    title: "Dungeons & Deejay, la rivelazione",
    where: "Galleria - 6 - 7",
    when: "Sabato 20 / ore 13:00",
    image: "https://picsum.photos/380/260",
    desc: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Quidem, vitae voluptatum. Beatae, quidem! Impedit culpa accusantium molestias eos voluptates. Laboriosam quidem explicabo eos, ratione laborum molestias vero odit similique recusandae! Ipsa deleniti iste quam est sequi, nulla libero rerum recusandae alias reprehenderit obcaecati repudiandae ea a assumenda laboriosam laudantium unde, explicabo beatae."
  },
];

</script>

<style scoped>
/* -------------------------------------------------------------- CONTAINER */
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

/* -------------------------------------------------------------- FLIPPER */
.flip-card {
  background-color: transparent;
  perspective: 1000px;

  width: 340px;
  height: 520px;
}
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.flip-card-back {
  transform: rotateY(180deg);
}

/* -------------------------------------------------------------- CARDS */
.flip-card-front, .flip-card-back {
  background: white;
  border-radius: 20px;
  max-width: 390px;
  border: 5px solid #b0082b;
  text-align: left;
}
.flip-card:first-of-type .flip-card-front, .flip-card:first-of-type .flip-card-back{
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

.flip-card:first-of-type .separator {
  background: grey;
}

p {
  color: grey;
}

.img-ct {
  position: relative;
  bottom: -10px;

  width: 100%;
}

img {
  border-bottom-right-radius: 15px;
  border-bottom-left-radius: 15px;
  width: 100%;
  height: 100%;
}

.desc {
  margin-bottom: 1rem;
  max-height: 200px;
  overflow: auto;
}


@media only screen and (max-width:980px) {

  .wrapper {
    flex-wrap: wrap;
  }

  h1 {
    font-size: 1.7rem;
  }

}
</style>