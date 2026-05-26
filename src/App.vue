<script setup>
import { ref, computed } from 'vue'
import { onMounted, onUnmounted } from 'vue'
import CD from '/src/icons/disc-spin.gif'
import TV from '/src/icons/gif_tv_dvd_5.gif'
import LEA from '/src/icons/Lea_3D_icon.png'
import Photo from '/src/icons/photo-album.png'
import ART from '/src/icons/render_000.png'


// ─── REMOVE all these local gif imports ───────────────────────────────────────
// import gif1 from '/src/dvd/DEMO_LEA_V4_4_1.gif'   ← delete these 19 lines
// ...
// import gif19 from '/src/dvd/new.gif'
// ─────────────────────────────────────────────────────────────────────────────

// ─── R2 CONFIG — only line you ever need to change ───────────────────────────
const R2 = 'https://pub-68ca04e89a04442090a6f0cd319f22c4.r2.dev'
// ─────────────────────────────────────────────────────────────────────────────


const gifs = {
  apophis:           `${R2}/Apophis_Onprendradel'avanceplustard.gif`,
bibiClubFeu:       `${R2}/BIBI_CLUB_FEU.gif`,
bibiClubNuit:      `${R2}/Bibi%20Clb_La%20Nuit.gif`,
bibiClubMatin:     `${R2}/Bibi%20Club_Le%20Matin.gif`,
bibiClubParasite:  `${R2}/Bibi%20Club_Parasite.gif`,
bibiClubFemme:     `${R2}/Bibi%20Club_femme%20lady.gif`,
bonEnfant:         `${R2}/Bon%20Enfant_minimum.gif`,
claudiaBouvette:   `${R2}/Claudia%20Bouvette_BBZ.gif`,
emily:             `${R2}/Emily.gif`,
goodbyeKarelle1:   `${R2}/Goodbye%20Karelle_Moonroad_OPTION_1.gif`,
goodbyeKarelle2:   `${R2}/GoodbyeKarelle_MoonRoad_OPTION_2.gif`,
hubertDimanche:    `${R2}/HUBERT_LENOIR_DIMANCHE%20SOIR.gif`,
hubertBunny:       `${R2}/Hubert%20Lenoir_Hunny%20Bunny.gif`,
hubertSecret:      `${R2}/Hubert%20Lenoir_Secret.gif`,
hubertULCC:        `${R2}/Hubert%20Lenoir_ULCC.gif`,
louAdrianne:       `${R2}/LOUADRIANNECASSIDY_LAPLUIENETOMBEJAMAISSURTOIy.gif`,
lysandre5052:      `${R2}/Lysandre_5052..gif`,
lysandre5052HD:    `${R2}/Lysandre_5052_Master_HD.gif`,
lysandrePluie:     `${R2}/Lysandre_lodeurdelapluie.gif`,
miroirNNao:        `${R2}/MIROIR_%20N%20NAO..gif`,
nNaoLive:          `${R2}/N%20NAO%20-%20Live%20Session.gif`,
patrickChurch:     `${R2}/Patrick-Chuch_Beauty-Story.gif`,
poisonResort:      `${R2}/Poison%20Resort_shortfilm.gif`,
robertRobert:      `${R2}/Robert%20Robert_L'e%CC%81te%CC%81%20je%20m'ennuie_.gif`,
sophiaBel:         `${R2}/Sophia%20Bel_2AM.gif`,
aoife:             `${R2}/aoife_nessa_frances_this_still_life.gif`,
claudeMckenzie:    `${R2}/claude_mckenzie.gif`,
geeseOption1:      `${R2}/geese_Taxes_UKVMA_OPTION_1.gif`,
geeseOption2:      `${R2}/geese_taxes_OPTION_2.gif`,
lysandrePaon:      `${R2}/lysandre_le_paon_impossible.gif`,
ofranda:           `${R2}/ofranda_shortfilm.gif`,
theHorrors:        `${R2}/the_horrors_ariel.gif`,
  
}






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
{ name: 'Show Reel', image: CD,
  content: [
    {type: 'vimeo', src: 'https://player.vimeo.com/video/842262667?badge=0&amp;autopause=0&amp;player_id=0&amp;app_id=58479'}
  ]
},
{ name: 'Motion Works', 
    image: TV, 
    branches: [
      {
        label: 'DIRECTING & DOP',
        tabs: [
          { label: 'Fashion', gifs: [gifs.emily, gifs.patrickChurch] },
          { label: 'Music Videos ', gifs: [gifs.bibiClubNuit, gifs.bibiClubFemme,gifs.bibiClubMatin, gifs.bibiClubParasite,
          gifs.bibiClubFeu, gifs.bonEnfant,gifs.claudiaBouvette, gifs.goodbyeKarelle1,gifs.goodbyeKarelle2, 
          gifs.lysandre5052,gifs.lysandre5052HD, gifs.lysandrePluie,
          gifs.sophiaBel,
          ] },
        ]
      },
      {
        label: 'DOP',
        tabs: [
          { label: 'Music Videos', gifs: [gifs.aoife, gifs.apophis, gifs.claudeMckenzie,
          gifs.geeseOption1, gifs.geeseOption2, gifs.hubertBunny, gifs.hubertSecret,
          gifs.hubertULCC, gifs.hubertDimanche, gifs.louAdrianne, gifs.lysandrePaon,
          gifs.miroirNNao, gifs.nNaoLive, gifs.robertRobert, gifs.theHorrors,
          ] },
          { label: 'Short films', gifs: [gifs.ofranda, gifs.poisonResort] },
        ]
      },
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
  branches: item.branches ?? null,
  id: nextId++,
  name: item.name,
  image: item.image,
  content: item.content ?? [],
  tabs: item.tabs ?? [],
  activeTab: item.tabs?.[0]?.id ?? null,
  activeBranch: 0,  // ← which branch button is active
  activeTab: 0,   
  branchSelected: false,
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
      ? { left: '0', top: '44px', width: '100vw', height: '100vh' }
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

  <div class="window-body">
        <menu role="tablist">
              <li
                v-for="tab in win.tabs"
                :key="tab.id"
                role="tab"
                :aria-selected="win.activeTab === tab.id"
                @click="win.activeTab = tab.id"
              >
                <a>{{ tab.label }}</a>
              </li>
        </menu>



    <!-- Branch buttons -->
    <div class="branch-controls">
      <button
        @click="win.activeBranch = 0; win.activeTab = 0; win.branchSelected = true"
        :class="{ active: win.activeBranch === 0 }"
      >DIRECTING & DOP</button>
      <button
        @click="win.activeBranch = 1; win.activeTab = 0; win.branchSelected = true"
        :class="{ active: win.activeBranch === 1 }"
      >DOP</button>
    </div>

    <!-- 98.css tabs -->
    <menu role="tablist"  :style="{ display: win.branchSelected ? 'flex' : 'none' }">
      <li
        v-for="(tab, t) in win.branches[win.activeBranch].tabs"
        :key="t"
        role="tab"
        :aria-selected="win.activeTab === t"
        @click="win.activeTab = t"
      >
        <a>{{ tab.label }}</a>
      </li>
    </menu>

    <div class="sunken-panel" :style="{ display: win.branchSelected ? 'flex' : 'none' }">
      <div
        v-for="gif in win.branches[win.activeBranch].tabs[win.activeTab].gifs"
        :key="gif"
        class="crop"
      >
        <img :src="gif" />
      </div>
    </div>



  </div>
  
</div>
  <footer class="window footer-window">
    <button @click="toggleMenu">Menu</button>
  </footer>

 

</div>
</template>

<style scoped>

menu {
  display: flex;
 flex-direction: row;
 align-content: center;
  width: 50%;
}

menu li {
  flex: 1 !important;
  text-align: center;
}



.title-bar {
  position: sticky;
  top: 0;
  z-index: 1;
}

header {
  display: flex;
  flex-direction: row!important;
}

#motionWindow{
  height:100%;
  border: none!important;

}

.branch-controls {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin-top: 5px;
  margin-bottom: 12px;
}

.branch-controls button {
  width: 100%!important;
  height: 30px;
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
  height:100%;
}

.sunken-panel {
  display: flex;
  flex-wrap: wrap;
  overflow-y: scroll;
  background-color:silver;
  height:100%;
}

.crop {
  width: 33%;
  aspect-ratio: 16/9;
  overflow: hidden;
  flex-shrink: 0;
}

.crop img {
  width: 100%;

  object-fit: cover;
  display: block;
}


.window-body img{
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
  height: 90%;
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
