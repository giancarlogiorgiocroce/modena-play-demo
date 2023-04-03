<template>
  <div class="ct">
    <div class="wrapper center">
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
        <Button class="btn" value="BIGLIETTI"/>
        <Button class="btn" name="material-symbols:person"/>

        <div class="hamburger">
          <span>MENU</span>
          <Icon class="icon" name="heroicons:bars-3-solid" />
        </div>
      </div>
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
</script>

<style scoped>
@media only screen and (min-width: 1280px) {
  .link {
    font-size: 1.3rem;
  }
}
.ct {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: white;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.wrapper {
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
  transition: all 0.3s ease-out;
}

.btns {
  display: flex;
  gap: 0.5rem;
}

.hamburger {
  display: none;
}

@media only screen and (max-width:980px) {
  .link {
    display: none;
  }

  .btn {
    display: none;
  }
  .hamburger {
    display: flex;
    gap: 0.5rem;
    color: #b0082b;
    font-weight: bold;
  }

  .hamburger span {
    display: flex;
    align-items: center;
  }

  .icon {
    width: 50px;
    height: 40px;
  }
}
</style>