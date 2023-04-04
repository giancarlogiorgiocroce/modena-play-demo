<template>
<div class="no-result flex-c">
  <div class="alert-ct flex-c">
    <icon class="icon" name="material-symbols:help" />
    <p class="title">Nessun risultato! Sembra che questa pagina sia ancora in lavorazione :D</p>
    <NuxtLink to="/">
      <Button value="Torna alla Home" inverted-colorscheme/>
    </NuxtLink>
  </div>
</div>
</template>

<style scoped>
.no-result {
  display: flex; justify-content: center;
  border-radius: 2.5rem;
  max-width: 700px; height: 100vh; padding: 2.5rem 0; margin: 0 auto;
}

.alert-ct {
  height: fit-content;
  padding: 3.5rem;
  text-align: center;
  gap: 1rem;
  box-shadow: 2px 2px 10px #b0082b;
  border-radius: 2.5rem;

  transition: all 2s;
}
.alert-ct > * {
  margin-bottom: 1rem;
}
.icon {
  color: #b0082b;
  height: 9rem;
  width: 9rem;
  fill: currentColor;

  transition: all 2s;
}
.alert-ct:hover .icon {
  height: 12rem;
  width: 12rem;
}
.title {
  font-size: 1.5rem; font-weight: bold;
}

@media only screen and (max-width: 980px) {
  .no-result {
    border-radius: 0;
    box-shadow: none;
  }

  .alert-ct {
    padding: 1rem;
  }
}
</style>
