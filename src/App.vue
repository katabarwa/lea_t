<script setup>
import { ref } from 'vue'
import { onMounted, onUnmounted } from 'vue'
import CD from './public/icons/disc-spin.gif'
import TV from './public/icons/gif_tv_dvd_4.gif'
import LEA from './public/icons/Lea_3D_icon.png'
import Photo from './public/icons/photo-album.png'
import ART from './public/icons/render_000.png'


const enter = ref(false)

const currentTime = ref('00:00:00')

let interval

const updateClock = () => {
  const now = new Date()

  currentTime.value = now.toLocaleTimeString('en-GB', {
    hour: '2-digit',
    minute: '2-digit',
    second: '2-digit'
  })
}

onMounted(() => {
  updateClock()

  interval = setInterval(() => {
    updateClock()
  }, 1000)
})

onUnmounted(() => {
  clearInterval(interval)
})

const menu = ref(false)

const toggleMenu = () => {
  menu.value = !menu.value
}

const icons = ref([
{ name: 'CD', image: CD},
{ name: 'TV', image: TV },
{ name: 'LEA', image: LEA },
{ name: 'Photo', image: Photo },
{ name: 'ART', image: ART },
])

</script>

<template>
<button  class="enter-button"     v-if="!enter" @click="enter = true">Enter</button>
<div class="main" v-if="enter">

  <header  class="window header-window">
    <button>Contact</button>
    <h3 class="title">Léa Taillefer</h3>
    <div class="clock">
        {{ currentTime }}
      </div>
  </header>
  <div class="menu" v-if="menu">
    <div class="window-body icon-grid">

<div
  v-for="item in icons"
  :key="item.name"
  class="icon-item"
>
  <img
    :src="item.image"
    :alt="item.name"
  />

  <span>
    {{ item.name }}
  </span>
</div>


</div>
  </div>
  <footer class="window footer-window">
    <button @click="toggleMenu">Start</button>
  </footer>

 

</div>
</template>

<style scoped>


.icon-item img {
  width: 250px;
  height: 250px;

  image-rendering: pixelated;
  display: block;
}
.icon-grid {
  width: 95%;
  height: 95%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;  
  flex-direction: row;
  gap: 12px;
  width: 100%;
  padding: 70px;
  overflow: hidden;
}

.main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100%;
  overflow-x: hidden;
}

.title {
  font-size: 0.7rem;
  font-weight: 600;
  margin: 0;
}

.clock {
  font-size: 0.7rem;
  font-weight: 600;
  margin-right: 5px;
}

header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.footer-window {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 100;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.enter-button {
  position: fixed;
  top: 50%;
  left: 50%;
  right: 50%;
  z-index: 100;
}
</style>
