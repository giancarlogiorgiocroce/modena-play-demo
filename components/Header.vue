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

        <div class="hamburger" @click="toggleSideMenu()">
          <span>MENU</span>
          <!-- <Icon class="icon" name="heroicons:bars-3-solid" @click="toggleSideMenu()"/> -->
          <div class="lines-ct" :class="{'opened': isSideMenuVisible}">
            <div class="line"></div>
            <div class="line"></div>
            <div class="line"></div>
          </div>
        </div>

        <div v-if="isSideMenuVisible" class="side-menu-bg"></div>
        <div :class="{'modal-active': isSideMenuVisible}" class="side-menu">
          <ul>
            <li @click="toggleInfoVisibility('PROGRAMMA')">PROGRAMMA</li>
            <li
              v-for="l in lorem"
              :key="l"
              :class="infoShowned.includes('PROGRAMMA') ? 'visible' : ''"
              >{{ l }}</li>
          </ul>
          <ul>
            <li @click="toggleInfoVisibility('NEWS')">NEWS</li>
            <li
              v-for="l in lorem" 
              :key="l"
              :class="infoShowned.includes('NEWS') ? 'visible' : ''"
              >{{ l }}</li>
          </ul>
          <ul>
            <li @click="toggleInfoVisibility('INFO')">INFO</li>
            <li 
              v-for="l in lorem" 
              :key="l"
              :class="infoShowned.includes('INFO') ? 'visible' : ''"
              >{{ l }}</li>
          </ul>
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
const lorem:string[] = ["Lorem", "ipsum", "dolor", "sit", "amet", "consectetur", "adipisicing", "elit."];
let isSideMenuVisible = ref(false);
let infoShowned = ref(["PROGRAMMA"]);

// METHODS
const toggleSideMenu = ():void => {
  isSideMenuVisible.value = !isSideMenuVisible.value
}
const toggleInfoVisibility = (id:string) => {
  if (!infoShowned.value.includes(id)) {
    infoShowned.value.push(id);
    console.log(id);
    
  } else {
    const index = infoShowned.value.indexOf(id);
    infoShowned.value.splice(index, 1);
  }
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
.side-menu-bg, .side-menu {
  width: 0;
  transition: none;

}

.side-menu > * {
  display: none;
}

@media only screen and (max-width:980px) {
  .link, .btn {
    display: none;
  }

  .btns {
    gap: 0;
  }
  .hamburger {
    display: flex;
    align-items: center;
    gap: 1rem;
    color: #b0082b;
    font-weight: bold;
    z-index: 9;

    height: 70px;
  }

  .hamburger span {
    display: flex;
    align-items: center;
    font-size: 18px;
  }

  .lines-ct {
    width: 20px;
    height: 20px;
  }

  .lines-ct.opened {
    transform: translateY(3px);
  }
  .lines-ct.opened .line:first-child {
    transform: rotate(45deg) translateY(5.5px);
  }
  .lines-ct.opened .line:nth-child(2) {
    display: none;
  }
  .lines-ct.opened .line:last-child {
    transform: rotate(-45deg) translateY(-5.5px);
  }

  .line {
    background-color: #b0082b;
    height: 4px;
    margin-bottom: 4px;
    border-radius: 2px;
    transition: transform 0.5s ease, color 0.5s ease, opacity 0.5s ease;
  }

  /* SIDE MENU */
  .side-menu-bg {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;

    width: 100%;

    background-color: rgba(255, 255, 255, 0.6);
  }
  .side-menu.modal-active {
    position: fixed;
    right: 0;
    top: 0;
    z-index: 8;

    display: block;

    width: 280px;
    height: 100vh;
    background-color: #fff;
    padding: 100px 30px;

    transition: width 0.5s ease-out;
  }
  .side-menu.modal-active ul {
    display: block;
    list-style-type: none;
    text-transform: capitalize;
    margin-left: 30px;
    margin-bottom: 20px;
    padding: 0;

    color: grey;
  }
  .side-menu.modal-active ul li:first-child {
    display: block;
    list-style-type: none;
    margin-left: -20px;
    margin-bottom: 20px;

    font-weight: bold;
    color: #b0082b;
  }
  .side-menu.modal-active ul li {
    display: none;
    cursor: pointer;
  }
  .side-menu.modal-active ul li.visible {
    display: block;
  }
}
</style>