<template>
  <div class="app">
    <Header />
    <Jumbotron />
    <CountDown />
    <Footer />
  </div>
</template>

<style>
* {
  box-sizing: border-box;
  text-decoration: none;
  font-family: sans-serif;
  font-size: 16px;
}

p {
  margin: 0;
}

ul {
  list-style-type: none;
  margin: 0;
}

.center {
  width: 90%;
  margin: 0 auto;
}

.bg-red {
  background-color: #b0082b;
}

.flex-c{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>