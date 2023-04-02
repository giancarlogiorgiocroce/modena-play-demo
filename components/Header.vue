<template>
  <div class="ct center">
    <div class="links-ct">
      <a class="img-ct" href="https://www.play-modena.it">
        <img src="../assets/logo-play-header.png" alt="logo">
      </a>
      <a href="" class="link">
        programma
      </a>
      <a 
        v-for="link in links" 
        :key="link.text"
        :href="link.href"
        class="link"
      >
        {{ link.text }}
      </a>
    </div>

    <div class="btns">
      Bottoni vari
    </div>
  </div>
</template>

<script setup lang="ts">
// DATA
const links:any = {
  two: {text:"news", href:"https://www.play-modena.it/news/" },
  three: {text:"informazioni", href:"https://www.play-modena.it/informazioni/" },
  four: {text:"press", href:"https://www.play-modena.it/press/" },
}
const getLog = (el:any) => {
  console.log(el);
}
</script>

<style scoped>
.ct {
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.img-ct {
  max-width: 130px;
  max-height: 60px;
}

.links-ct{
  display: flex;
  gap: 2rem;
}

.link {
  display: block;
  text-transform: uppercase;
  color: #b0082b;
  margin: auto 0;
  font-weight: bold;
}

@media only screen and (max-width:980px) {
  .link {
    display: none;
  }
}
</style>