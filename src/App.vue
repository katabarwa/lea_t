<script setup>
import { ref } from 'vue'
import { onMounted, onUnmounted } from 'vue'
import CD from '/src/icons/disc-spin.gif'
import TV from '/src/icons/gif_tv_dvd_5.gif'
import LEA from '/src/icons/Lea_3D_icon.png'
import Photo from '/src/icons/photo-album.png'
import ART from '/src/icons/render_000.png'
import gif1 from '/src/dvd/DEMO_LEA_V4_4_1.gif'
import gif2 from '/src/dvd/DEMO_LEA_V4_5_1.gif'
import gif3 from '/src/dvd/DEMO_LEA_V4_6_1.gif'
import gif4 from '/src/dvd/DEMO_LEA_V4_7_1.gif'
import gif5 from '/src/dvd/DEMO_LEA_V4_8_1.gif'
import gif6 from '/src/dvd/DEMO_LEA_V4_9_1.gif'
import gif7 from '/src/dvd/DEMO_LEA_V4_10_1.gif'
import gif8 from '/src/dvd/DEMO_LEA_V4_11_1.gif'
import gif9 from '/src/dvd/DEMO_LEA_V4_12_1.gif'
import gif10 from '/src/dvd/DEMO_LEA_V4_13_1.gif'
import gif11 from '/src/dvd/DEMO_LEA_V4_14_1.gif'
import gif12 from '/src/dvd/DEMO_LEA_V4_15_1.gif'
import gif13 from '/src/dvd/lea-gif-1.gif'
import gif14 from '/src/dvd/lea-gif-2.gif'
import gif15 from '/src/dvd/lea-gif-3.gif'
import gif16 from '/src/dvd/lea-gif-4.gif'
import gif17 from '/src/dvd/lea-gif-5.gif'
import gif18 from '/src/dvd/lea-gif-6.gif'
import gif19 from '/src/dvd/new.gif'





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

const menu = ref(true)

const toggleMenu = () => {
  menu.value = !menu.value
}

function toggleMinimize() {
  fullscreen.value = false
  minimized.value = !minimized.value
}
 
function toggleFullscreen() {
  minimized.value = false
  fullscreen.value = !fullscreen.value
}

const icons = ref([
{ name: 'Show Reel', image: CD},
{ name: 'Motion Works', 
    image: TV, 
    content: [
      { type: 'image', src: gif1},
      { type: 'image', src:gif2 },
      { type: 'image', src:gif3 },
      { type: 'image', src:gif4 },
      { type: 'image', src:gif5 },
      { type: 'image', src:gif6 },
      { type: 'image', src:gif7  },
      { type: 'image', src:gif8  },
      { type: 'image', src:gif9  },
      { type: 'image', src:gif10  },
      { type: 'image', src:gif11  },
      { type: 'image', src:gif12  },
      { type: 'image', src:gif13 },
      { type: 'image', src:gif14 },
      { type: 'image', src:gif15 },
      { type: 'image', src:gif16 },
      { type: 'image', src:gif17 },
      { type: 'image', src:gif18 },
      { type: 'image', src:gif19 },
    ]
  },
{ name: 'Biography', image: LEA },
{ name: 'Photography', image: Photo },
{ name: 'ART', image: ART },
])

// Track open windows as an array of objects




const openWindows = ref([])
let nextId = 0

function openWindow(item) {
  const alreadyOpen = openWindows.value.find(w => w.name === item.name)
  if (alreadyOpen) {
    alreadyOpen.focused = true
    return
  }



openWindows.value.push({
    id: nextId++,
    name: item.name,
    image: item.image,
    content: item.content ?? [],
    focused: true,
    minimized: false,
    maximized: false,
    x: window.innerWidth * 0.5 + Math.random() * window.innerWidth * 0.1 - 300,
    y: window.innerHeight * 0.5 + Math.random() * window.innerHeight * 0.1 - 225,
  })
}

function closeWindow(id) {
  openWindows.value = openWindows.value.filter(w => w.id !== id)
}
function minimizeWindow(id) {
  const win = openWindows.value.find(w => w.id === id)
  if (win) win.minimized = !win.minimized
  win.maximized = false 
}

function maximizeWindow(id) {
  const win = openWindows.value.find(w => w.id === id)
  if (win) win.maximized = !win.maximized
  win.minimized = false
}

function focusWindow(id) {
  openWindows.value.forEach(w => w.focused = w.id === id)
}

const open       = ref(false)
const minimized  = ref(false)
const fullscreen = ref(false)

function startDrag(event, win) {
  if (win.maximized) return  // don't drag maximized windows

  const startX = event.clientX - win.x
  const startY = event.clientY - win.y

  function onMove(e) {
    win.x = e.clientX - startX
    win.y = e.clientY - startY
  }

  function onUp() {
    window.removeEventListener('mousemove', onMove)
    window.removeEventListener('mouseup', onUp)
  }

  window.addEventListener('mousemove', onMove)
  window.addEventListener('mouseup', onUp)
}

</script>

<template>
<button  class="enter-button"     v-if="!enter" @click="enter = true">Enter</button>
<div class="main" v-if="enter">

  <header  class="window header-window">
    <button v-if="!open" @click="open = true">Contact</button>
    <button disabled v-if="open" @click="open = true">Contact</button>


<div class="titleWrapper">
  <h3 class="title">Léa Taillefer</h3>
</div>
  <div class="clock">
        {{ currentTime }}
  </div>


  </header>

  <div v-if="open" class="window" :class="{ minimized, fullscreen }"  style="width: 350px" >
    <div  >
      <div class="title-bar">
        <div class="title-bar-text">Contact</div>
        <div class="title-bar-controls">
          <button @click="toggleMinimize" aria-label="Minimize"></button>
          <button @click="toggleFullscreen" aria-label="Maximize"></button>
          <button @click="open = false" aria-label="Close"></button>
        </div>
      </div>
      <div v-if="!minimized" class="content"><a href="Mailto:americanlean@gmail.com">americanlean@gmail.com</a>
        <a href="">VIMEO</a>
      </div>
    </div>
  </div>


       <!-- Menu (icons only) -->
<div class="menu" v-if="menu">
  <div class="window-body icon-grid">
    <div
      v-for="item in icons"
      :key="item.name"
      class="icon-item"
      @click="openWindow(item)"
    >
      <img :src="item.image" :alt="item.name" />
      <div class="iconTitle">
        <span>{{ item.name }}</span>
      </div>

    </div>
  </div>
</div>

<!-- Windows (always rendered, outside menu) -->
<div class="window" id="menuWindow"
  v-for="win in openWindows"
  :key="win.id"
  :style="{
    position: 'absolute',
    zIndex: win.focused ? 10 : 1,
    ...(win.maximized
      ? { left: '0', top: '44px', width: '100vw', height: '90vh' }
      : win.minimized
        ? { left: win.x + 'px', top: win.y + 'px', height: '44px', overflow: 'hidden' }
        : { left: win.x + 'px', top: win.y + 'px' }
    )
  }"
  @mousedown="focusWindow(win.id)"
  :class="{
    'is-focused': win.focused,
    'is-minimized': win.minimized,
    'is-maximized': win.maximized,
  }"
>
  <div class="title-bar" @mousedown="startDrag($event, win)">
    <span>{{ win.name }}</span>
    <div class="title-bar-controls">
      <button @click="minimizeWindow(win.id)" aria-label="Minimize"></button>
      <button @click="maximizeWindow(win.id)" aria-label="Maximize"></button>
      <button @click="closeWindow(win.id)" aria-label="Close"></button>
    </div>
  </div>

  <div class="window-body" v-show="!win.minimized">
    <div class="sunken-panel" >
      <template v-for="(media, index) in win.content" :key="index">
      <img   v-if="media.type === 'image'" :src="media.src" width="200px"/>
      <video v-else-if="media.type === 'video'" :src="media.src" controls />
      <audio v-else-if="media.type === 'audio'" :src="media.src" controls />
      <p     v-else-if="media.type === 'text'">{{ media.src }}</p>
    </template>
    </div>

  </div>
</div>
  <footer class="window footer-window">
    <button @click="toggleMenu">Menu</button>
  </footer>

 

</div>
</template>

<style scoped>

.title-bar {
  position: sticky;
  top: 0;
  z-index: 1;
}

.window {
  overflow: hidden;
  display: flex;
  flex-direction: column;
  max-height: 80vh;
}

.window-body {
  flex: 1;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.sunken-panel {
  flex: 1;
  overflow-y: scroll;
  background-color:rgb(204, 204, 204);
}

.window-body img{
  width:185px;
  padding: 3px;
  border-radius: 10px;
}

.window .title-bar {
  color: azure;
  font-weight: 900;
}

.window .title-bar span{
  width: 100%;
  text-align: center;
}

#menuWindow {
  width: 600px;
  height: 450px;
}



.icon-grid .icon-item img{
  cursor: pointer;
}

.icon-item {
  color:cornflowerblue ;
  text-align: center;
}

.iconTitle {
  margin-top: 5px;
}

window.fullscreen {
  width: 100%;
}

.titleWrapper {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.content {
  margin: 50px;
  display: flex;
  flex-direction: column;
  align-content: center;
  text-align: center;
}

.icon-item img {
  width: 11em;
  height: 11em;

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
  gap: 50px;
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
  display: flex;
  flex-direction: row;
  align-items: center;
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
