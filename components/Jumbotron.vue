<template>
  <div class="ct bg-red">
    <div class="img-ct">
      <img src="../assets/play-logo-jtron.png" alt="jumbo">
    </div>
  </div>
</template>

<style scoped>
.ct {
  height: 100vh;
  margin-top: 70px;
  background-image: url("../assets/play-monster.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
.img-ct {
  position: relative;
  left: 60%;
  top: 10%;

  height: 500px;
  width: 300px;
}

.img-ct img {
  max-height: 100%;
}

@media only screen and (max-width:980px) {
  .ct {
    background-image: none;
    background-color: b0082b;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .img-ct {
    position: static;
  }
}
</style>