<script setup>
import { ref, computed } from 'vue'
import { onMounted, onUnmounted } from 'vue'
import CD from '/src/icons/disc-spin.gif'
import TV from '/src/icons/gif_tv_dvd_5.gif'
import LEA from '/src/icons/Lea_3D_icon.png'
import Photo from '/src/icons/photo-album.png'
import ART from '/src/icons/render_000.png'
import SDTE from '/src/assets/sdte.gif'
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

const photos = {
  newBondStreet1: `${R2}/15%20new%20bond%20street_editorial_pulsemag_1.jpg`,
  newBondStreet2: `${R2}/15%20new%20bond%20street_editorial_pulsemag_2.jpg`,
  newBondStreet3: `${R2}/15%20new%20bond%20street_editorial_pulsemag_3.jpg`,
  newBondStreet5: `${R2}/15%20new%20bond%20street_editorial_pulsemag_5.jpg`,
  newBondStreet4:          `${R2}/15%20new%20bond%20street_editorial_pulsemag_4.jpg`,
  newBondStreet6:          `${R2}/15%20new%20bond%20street_editorial_pulsemag_6.jpg`,
  newBondStreetPulsemag1: `${R2}/15%20new%20bond%20street_pulsemag1.png`,
newBondStreetPulsemag2: `${R2}/15%20new%20bond%20street_pulsemag2.png`,
newBondStreetPulsemag3: `${R2}/15%20new%20bond%20street_pulsemag3.png`,
albumCoverArjunaOakes2019: `${R2}/Album%20Cover_Arjuna%20Oakes_2019.jpg`,
albumCoverDJFuckoff2025:   `${R2}/Album%20cover_DJ%20Fuckoff_2025.jpg`,
albumCoverPhoebeJames:     `${R2}/Album%20cover_Phoebe_james.jpg`,
  aime2024:                `${R2}/Aime%CC%81_2024.jpg`,
  albumCoverArianeRoy:     `${R2}/Album%20cover_Ariane_Roy_2024_8.JPG`,
  albumCoverReflexiones:   `${R2}/Album%20cover_reflexiones_gabriella_olivo_2026.jpg`,
  alexa:                   `${R2}/Alexa.jpg`,
  aotearoa2018:            `${R2}/Aotearoa-2018.jpg`,
  aotearoa2023:            `${R2}/Aotearoa_2023.jpg`,
  atallephdreony:          `${R2}/Atalleph%20Dreony_2021.jpg`,
  asbDocumentationW1:          `${R2}/ASB_documentation_W_1.jpg`,
asbDocumentationAtalleph2:   `${R2}/ASB_documentation_atalleph_2.jpg`,
asbDocumentationAtalleph3:   `${R2}/ASB_documentation_atalleph_3.jpg`,
asbDocumentationAtalleph4:   `${R2}/ASB_documentation_atalleph_4.jpg`,
asbDocumentationCrucifixion1:`${R2}/ASB_documentation_crucifixion_1.jpg`,
asbDocumentationCrucifixion2:`${R2}/ASB_documentation_crucifixion_2.jpg`,
asbDocumentationCrucifixion4:`${R2}/ASB_documentation_crucifixion_4.jpg`,
asbDocumentationHand1:       `${R2}/ASB_documentation_hand_1.jpg`,
asbDocumentationHand2:       `${R2}/ASB_documentation_hand_2.jpg`,
asbDocumentationKnife1:      `${R2}/ASB_documentation_knife_1.jpg`,
asbDocumentationKnife2:      `${R2}/ASB_documentation_knife_2.jpg`,
asbDocumentationMarks1:      `${R2}/ASB_documentation_marks_1.jpg`,
asbDocumentationMarks2:      `${R2}/ASB_documentatio`,
  btsYseult1:              `${R2}/BTS-photo_Yseult_1.jpg`,
  btsYseult2:              `${R2}/BTS-photo_Yseult_2.jpg`,
  btsYseult3:              `${R2}/BTS-photo_Yseult_3.jpg`,
  btsPomme:                `${R2}/BTS_pomme.jpg`,
  btsSylvain1:             `${R2}/BTS_simple%20comme%20sylvain_1.jpg`,
  btsSylvain2:             `${R2}/BTS_simple%20comme%20sylvain_2.jpg`,
  btsYseult1: `${R2}/BTS-photo_Yseult_1.jpg`,
btsYseult2: `${R2}/BTS-photo_Yseult_2.jpg`,
btsYseult3: `${R2}/BTS-photo_Yseult_3.jpg`,
btsPomme:   `${R2}/BTS_pomme.jpg`,
btsSylvain1:`${R2}/BTS_simple%20comme%20sylvain_1.jpg`,
btsSylvain2:`${R2}/BTS_simple%20comme%20sylvain_2.jpg`,
  blueSpring2022:          `${R2}/Blue%20Spring_2022.jpg`,
  bootlegger1:             `${R2}/Bootlegger_Magazine_Editorial_2024_1.jpg`,
  bootlegger2:             `${R2}/Bootlegger_Magazine_Editorial_2024_2.jpg`,
  bootlegger3:             `${R2}/Bootlegger_Magazine_Editorial_2024_3.jpg`,
  bootlegger4:             `${R2}/Bootlegger_Magazine_Editorial_2024_4.jpg`,
  bootlegger5:             `${R2}/Bootlegger_Magazine_Editorial_2024_5.jpg`,
  bootlegger6:             `${R2}/Bootlegger_Magazine_Editorial_2024_6.jpg`,
  bootlegger7:             `${R2}/Bootlegger_Magazine_Editorial_2024_7.jpg`,
  bootlegger8:             `${R2}/Bootlegger_Magazine_Editorial_2024_8.jpg`,
  bootlegger9:             `${R2}/Bootlegger_Magazine_Editorial_2024_9.jpg`,
  bootlegger10:            `${R2}/Bootlegger_Magazine_Editorial_2024_10.jpg`,
  bootlegger11:            `${R2}/Bootlegger_Magazine_Editorial_2024_11.jpg`,
  bootlegger12:            `${R2}/Bootlegger_Magazine_Editorial_2024_12.jpg`,
  britney2024:             `${R2}/Britney_2024.jpg`,
  calissa2019:             `${R2}/CALISSA_2019.jpg`,
  calissaTeiniker2019:     `${R2}/Calissa%20Teiniker_2019.jpg`,
  calissaPiha1:            `${R2}/Calissa%20Teiniker_Piha-_1.jpg`,
  calissaPiha4copy:        `${R2}/Calissa%20Teiniker_Piha-_4%20copy.jpg`,
  calissaPiha5:            `${R2}/Calissa%20Teiniker_Piha-_5.jpg`,
  calissaPiha7:            `${R2}/Calissa%20Teiniker_Piha-_7.jpg`,
  calissaPiha8:            `${R2}/Calissa%20Teiniker_Piha-_8.jpg`,
  calissaPiha:             `${R2}/Calissa%20Teiniker_Piha.jpg`,
  carole2019:              `${R2}/Carole_2019.jpg`,
  chloe2024:               `${R2}/Chloe_2024.jpg`,
  claudia2023_1:           `${R2}/Claudia_2023_1.jpg`,
  claudia2023_2:           `${R2}/Claudia_2023_2.jpg`,
  claudia2023_3:           `${R2}/Claudia_2023_3.jpg`,
  claudia2023_4:           `${R2}/Claudia_2023_4.jpg`,
  claudia4:                `${R2}/Claudia_4.jpg`,
  claudiaAcrylicTransfer:  `${R2}/Claudia_acrylic%20transfer_2023.jpg`,
  crystal2019:             `${R2}/Crystal_2019.jpg`,
  documentationArchives1: `${R2}/Documentation_Archives_2025_1.jpg`,
documentationArchives2: `${R2}/Documentation_Archives_2025_2.jpg`,
documentationArchives3: `${R2}/Documentation_Archives_2025_3.jpg`,
documentationArchives4: `${R2}/Documentation_Archives_2025_4.jpg`,
documentationArchives5: `${R2}/Documentation_Archives_2025_5.jpg`,
documentationArchives6: `${R2}/Documentation_Archives_2025_6.jpg`,
documentationArchives7: `${R2}/Documentation_Archives_2025_7.jpg`,
documentationArchives8: `${R2}/Documentation_Archives_2025_8.jpg`,
documentationArchives9: `${R2}/Documentation_Archives_2025_9.jpg`,
  dreony2020_1:            `${R2}/Dreony_2020_1.jpg`,
  dreony2020_2:            `${R2}/Dreony_2020_2.jpg`,
  femmeFatale1:            `${R2}/Femme%20Fatale_1.jpg`,
  femmeFatale2:            `${R2}/Femme%20Fatale_2.jpg`,
  femmeFatale3:            `${R2}/Femme%20Fatale_3.jpg`,
  hotNCold2023:            `${R2}/Hot%20n%20Cold_2023.jpg`,
  hubertLenoir_interview0: `${R2}/Hubert%20Lenoir_interview_mag_2021_0.png`,
  hubertLenoir_interview1: `${R2}/Hubert%20Lenoir_Interview_mag_2021_1.jpg`,
  hubertLenoir_interview2: `${R2}/Hubert%20Lenoir_Interview_mag_2021_2.jpg`,
  hubertLenoir_interview3: `${R2}/Hubert%20Lenoir_Interview_mag_2021_3.jpg`,
  hubertLenoir_interview4: `${R2}/Hubert%20Lenoir_Interview_mag_2021_4.jpg`,
  hunnyBunny2019:          `${R2}/Hunny%20Bunny_2019.jpg`,
  kanePortraits26:         `${R2}/KANE%20PORTRAITS%2026.jpg`,
  imageAssetCopy: `${R2}/image-asset%20copy.jpg`,
  kane2019:                `${R2}/Kane_2019.jpg`,
  linvincibleBTS1:         `${R2}/L'invincible_BTS_photos_2021_1.jpg`,
  linvincibleBTS2:         `${R2}/L'invincible_BTS_photos_2021_2.jpg`,
  linvincibleBTS3:         `${R2}/L'invincible_BTS_photos_2021_3.jpg`,
  linvincibleBTS4:         `${R2}/L'invincible_BTS_photos_2021_4.jpg`,
  linvincibleBTS5:         `${R2}/L'invincible_BTS_photos_2021_5.jpg`,
  linvincibleBTS6:         `${R2}/L'invincible_BTS_photos_2021_6.jpg`,
  linvincibleBTS7:         `${R2}/L'invincible_BTS_photos_2021_7.jpg`,
  linvincibleBTS8:         `${R2}/L'invincible_BTS_photos_2021_8.jpg`,
  linvincibleBTS9:         `${R2}/L'invincible_BTS_photos_2021_9.jpg`,
  linvincibleBTS10:        `${R2}/L'invincible_BTS_photos_2021_10.jpg`,
  linvincibleBTS11:        `${R2}/L'invincible_BTS_photos_2021_11.jpg`,
  linvincibleBTS12:        `${R2}/L'invincible_BTS_photos_2021_12.jpg`,
  louis2018:               `${R2}/Louis_2018.jpg`,
  louis2019:               `${R2}/Louis_2019.jpg`,
  lucaPiscopo2022:         `${R2}/Luca%20piscopo_2022.jpg`,
  luca2022:                `${R2}/Luca_2022.jpg`,
  mixmagDJFuckoff1:        `${R2}/MIXMAG_DJFUCKOFF_1.png`,
  mixmagDJFuckoff2:        `${R2}/MIXMAG_DJFUCKOFF_2.jpg`,
  mixmagDJFuckoff3:        `${R2}/MIXMAG_DJFUCKOFF_3.jpg`,
  mixmagDJFuckoff4:        `${R2}/MIXMAG_DJFUCKOFF_4.jpg`,
  mixmagDJFuckoff5:        `${R2}/MIXMAG_DJFUCKOFF_5.jpg`,
  melissaVanDerAuf:        `${R2}/Melissa_van_der_auf_Greatest_Basslines_2025.jpg`,
  mincaColumbia2017:       `${R2}/Minca_Columbia_2017.jpg`,
  mincaColombia2017:       `${R2}/Minca_colombia_2017.jpg`,
  october2019:             `${R2}/October_2019.jpg`,
  october2019_2:           `${R2}/October_2019_2.jpg`,
  oliviaBrethault1:        `${R2}/Olivia%20Brethault_editorial_2019_1.jpg`,
  oliviaBrethault2:        `${R2}/Olivia%20Brethault_editorial_2019_2.jpg`,
  oliviaBrethault3:        `${R2}/Olivia%20Brethault_editorial_2019_3.jpg`,
  oliviaBrethault4:        `${R2}/Olivia%20Brethault_editorial_2019_4.jpg`,
  oliviaBrethault5:        `${R2}/Olivia%20Brethault_editorial_2019_5.jpg`,
  oliviaBrethault6:        `${R2}/Olivia%20Brethault_editorial_2019_6.jpg`,
  oliviaBrethault7:        `${R2}/Olivia%20Brethault_editorial_2019_7.jpg`,
  outtakeCommissionLivre:  `${R2}/Outtake%20commission%20livre_2023.jpg`,
  postMagCoverMars2020:    `${R2}/Post%20mag%20cover%20Mars%20issue%202020.jpg`,
  
  putAShirtOn:               `${R2}/PUT%20A%20SHIRT%20ON.jpg`,
putAShirtOn10:             `${R2}/PUT%20A%20SHIRT%20ON_10.jpg`,
putAShirtOn11:             `${R2}/PUT%20A%20SHIRT%20ON_11.jpg`,
putAShirtOn12:             `${R2}/PUT%20A%20SHIRT%20ON_12.jpg`,
putAShirtOn13:             `${R2}/PUT%20A%20SHIRT%20ON_13.jpg`,
putAShirtOn2:              `${R2}/PUT%20A%20SHIRT%20ON_2.jpg`,
putAShirtOn3:              `${R2}/PUT%20A%20SHIRT%20ON_3.jpg`,
putAShirtOn5:              `${R2}/PUT%20A%20SHIRT%20ON_5.jpg`,
putAShirtOn6:              `${R2}/PUT%20A%20SHIRT%20ON_6.jpg`,
putAShirtOn7:              `${R2}/PUT%20A%20SHIRT%20ON_7.jpg`,
putAShirtOn8:              `${R2}/PUT%20A%20SHIRT%20ON_8.jpg`,
putAShirtOn9:              `${R2}/PUT%20A%20SHIRT%20ON_9.jpg`,
putAShirtOnDocumentation:  `${R2}/PUT%20A%20SHIRT%20ON_DOCUMENTATION.jpg`,
putAShirtOnFlyer:          `${R2}/PUT%20A%20SHIRT%20ON_flyer.jpg`,
// 2019
pp1:  `${R2}/Press%20photo_Hubert%20Lenoir_2019.jpg`,
pp2:  `${R2}/Press%20photo_Leith%20Towers_2019_1.jpg`,
pp3:  `${R2}/Press%20photo_Leith%20Towers_2019_2.jpg`,

// 2020
pp4:  `${R2}/Press%20photo_Choses%20Sauvages_2020.jpg`,

// 2021
pp5:  `${R2}/Press%20photo_Traffic%20des%20airs_2021.jpg`,
pp6:  `${R2}/Press%20photo_%20Sophia%20Bel_2021.jpg`,

// no year / undated
pp7:  `${R2}/Press%20photo_Ringlets.jpg`,
pp8:  `${R2}/Press%20photo_Traffic%20des%20Airs%20copy.jpg`,
pp9:  `${R2}/Press%20photo_Traffic%20des%20airs.jpg`,
pp10: `${R2}/Press%20photo%20N%20NAO.jpg`,
pp11: `${R2}/Press%20photo_Queenie%20Jr_1.jpg`,
pp12: `${R2}/Press%20photo_Queenie%20Jr_2.jpg`,
pp13: `${R2}/Press%20photo_Queenie_Jr_3.jpg`,
pp14: `${R2}/Press_photo_DJFUCKOFF_1.jpg`,
pp15: `${R2}/Press_photo_DJFUCKOFF_2.jpg`,
pp16: `${R2}/Press_photo_DJFUCKOFF_3.jpg`,

// 2023
pp17: `${R2}/Press%20photo_%20N%20NAO_2023_1.jpg`,
pp18: `${R2}/Press%20photo_%20N%20NAO_2023_2.jpg`,
pp19: `${R2}/Press%20photo_%20N%20NAO_2023_3.jpg`,
pp20: `${R2}/Press%20photo_%20N%20NAO_2023_4.jpg`,
pp21: `${R2}/Press%20photo_%20N%20NAO_2023_5.jpg`,
pp22: `${R2}/Press%20photo_Ringlets_2023.jpeg`,
pp23: `${R2}/Press%20Photo_Ringlets_2023_2.jpg`,
pp24: `${R2}/Press%20Photo_Ringlets_2023_3.jpg`,
pp25: `${R2}/Press%20photo_Stoylov_1.jpg`,
pp26: `${R2}/Press%20photo_Stoylov_2.jpg`,
pp27: `${R2}/Press%20photo_Stoylov_3.jpg`,
pp28: `${R2}/Press%20photo_Stoylov_4.jpg`,
pp29: `${R2}/Press%20photo_Stoylov_5.jpg`,

// 2024
pp30: `${R2}/Press%20photo_Ariane_Roy_2024.jpg`,
pp31: `${R2}/Press%20photo_Ariane_Roy_2024_1.JPG`,
pp32: `${R2}/Press%20photo_Ariane_Roy_2024_2.JPG`,
pp33: `${R2}/Press%20photo_Ariane_Roy_2024_3.JPG`,
pp34: `${R2}/Press%20photo_Ariane_Roy_2024_4.JPG`,
pp35: `${R2}/Press%20photo_Ariane_Roy_2024_5.JPG`,
pp36: `${R2}/Press%20photo_Ariane_Roy_2024_6.JPG`,
pp37: `${R2}/Press%20photo_Ariane_Roy_2024_7.JPG`,
pp38: `${R2}/Press%20photo_Ariane_Roy_2024_9.JPG`,
pp39: `${R2}/Press%20photo_Ariane_Roy_2024_10.JPG`,
pp40: `${R2}/Press%20photo_Bon%20Enfant_2024_1.jpg`,
pp41: `${R2}/Press%20photo_Bon%20Enfant_2024_2.jpg`,
pp42: `${R2}/Press%20photo_N%20NAO%202024_1.jpg`,
pp43: `${R2}/Press%20photo_N%20NAO%202024_2.jpg`,
pp44: `${R2}/Press%20photo_N%20NAO%202024_3.jpg`,
pp45: `${R2}/Press%20photo_N%20NAO%202024_4.jpg`,

// 2025
pp46: `${R2}/Press%20photo_Kat_pereira_2025_1.jpg`,
pp47: `${R2}/Press%20photo_Kat_pereira_2025_2.jpg`,
pp48: `${R2}/Press%20photo_Kat_pereira_2025_3.jpg`,
pp49: `${R2}/Press%20photo_Kat_pereira_2025_4.jpg`,
pp50: `${R2}/Press%20photo_Kat_pereira_2025_5.jpg`,

// 2026
pp51: `${R2}/Press%20photo_Gabriella_Olivo_2026_1.jpg`,
pp52: `${R2}/Press%20photo_Gabriella_Olivo_2026_2.jpg`,
pp53: `${R2}/Press%20photo_Gabriella_Olivo_2026_3.jpg`,
pp54: `${R2}/Press%20photo_Gabriella_Olivo_2026_4.jpg`,
pp55: `${R2}/Press%20photo_Gabriella_Olivo_2026_5.jpg`,
pp56: `${R2}/Press%20photo_Gabriella_Olivo_2026_6.jpg`,
pp57: `${R2}/Press%20photo_N%20NAO_2026_1.jpg`,
pp58: `${R2}/Press%20photo_N%20NAO_2026_2.jpg`,
pp59: `${R2}/Press%20photo_N%20NAO_2026_3.jpg`,
pp60: `${R2}/Press%20photo_N%20NAO_2026_4.jpg`,
pp61: `${R2}/Press%20photo_N%20NAO_2026_5.jpg`,
pp62: `${R2}/Press%20photo_N%20NAO_2026_6.jpg`,

renForShortBTS:            `${R2}/REN%20FOR%20SHORT%20BTS%20PHOTO.jpg`,
secretArnaud:              `${R2}/SECRET-ARNAUD.jpg`,
secretCarole:              `${R2}/SECRET-CAROLE.jpg`,
secretHubert:              `${R2}/SECRET-HUBERT.jpg`,
secretNoemie:              `${R2}/SECRET-NO%C3%89MIE.jpg`,
stephenMarr2019:           `${R2}/STEPHEN%20MARR_2019.jpg`,
stephenMarr2019_2:         `${R2}/STEPHEN%20MARR_2019_2jpg.jpg`,
samuelGougoux2019:         `${R2}/Samuel%20Gougoux_2019.jpg`,
sculptura1:                `${R2}/Sculptura_1.jpg`,
sculptura2:                `${R2}/Sculptura_2.jpg`,
sculptura3:                `${R2}/Sculptura_3.jpg`,
sculptura4:                `${R2}/Sculptura_4.jpg`,
sculptura5:                `${R2}/Sculptura_5.jpg`,
sculptura6:                `${R2}/Sculptura_6.jpg`,
sculptura7:                `${R2}/Sculptura_7.jpg`,
sculptura8:                `${R2}/Sculptura_8.jpg`,
singleCoverStoylov:        `${R2}/Single%20Cover_Stoylov.jpg`,
strength2019:              `${R2}/Strenght_2019.jpg`,
synchronMagazine:          `${R2}/Synchron%20magazine%20together.jpg`,
thailand2018:              `${R2}/Thailand_2018.jpg`,
variationsOnFeet:          `${R2}/Variations%2Bon%2B_on%2Bfeet%2Bunder%2Bthe%2Btable%2Bhappen%2Bto%2Bbrush%2Bagainst%2Beach%2Bother_.jpg`,
variationsOnFeet1:         `${R2}/Variations%2Bon%2B_on%2Bfeet%2Bunder%2Bthe%2Btable%2Bhappen%2Bto%2Bbrush%2Bagainst%2Beach%2Bother_1.jpg`,
variationsOnFeet2:         `${R2}/Variations%2Bon%2B_on%2Bfeet%2Bunder%2Bthe%2Btable%2Bhappen%2Bto%2Bbrush%2Bagainst%2Beach%2Bother_2.jpg`,
vestibule2023_1:           `${R2}/Vestibule_2023_1.jpg`,
vestibule2023_2:           `${R2}/Vestibule_2023_2.jpg`,
vogueItaly:                `${R2}/Vogue%20Italy.jpg`,
vogueItaly1:               `${R2}/Vogue%20Italy_1.jpg`,
vogueItaly2:               `${R2}/Vogue%20Italy_2.jpg`,
}

const loadingGif = ref(null)        // which item is queued
const gifDone = ref(false)

const SDTE_DURATION = 2800   

const dropdownOpen = ref(false)




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
      { name: 'Motion Work', 
          image: TV,  type: 'motion',
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
      { name: 'Biography', image: LEA,
        type: 'bio',
  text: `LÉA TAILLEFER IS A MONTRÉAL AND LONDON-BASED MULTIDISCIPLINARY ARTIST, FILMMAKER, CINEMATOGRAPHER AND PHOTOGRAPHER WORKING ACROSS ART, FILM, MUSIC AND FASHION.

SHE HAS WORKED WITH ARTISTS SUCH AS HUBERT LENOIR, GEESE, ARIANE ROY, LOU-ADRIANE CASSIDY, BON ENFANT, CLAUDIA BOUVETTE AND GAB BOIS, AND HAS COLLABORATED WITH DIRECTORS INCLUDING NOEL PAUL, NOÉMIE D. LECLERC, VJOSANA SHKURTI AND LUCA PISCOPO. HER MUSIC VIDEO CINEMATOGRAPHY HAS BEEN SHORTLISTED AT THE UK MUSIC VIDEO AWARDS AND THE 1.4 AWARDS.

HER WORK HAS BEEN SHOWN INTERNATIONALLY IN SOLO AND GROUP EXHIBITIONS IN MONTRÉAL, AUCKLAND, NEW YORK AND GATINEAU, AND HAS APPEARED ACROSS PUBLICATIONS SUCH AS INTERVIEW, PAPER, PHOTO VOGUE ITALIA, ROLLING STONE, MIXMAG, AND CONTRIBUTOR MAGAZINE.`
       },
      { name: 'Photography', image: Photo, type: 'photos',
      tabs: [
          { label: 'Press Photos', photos: [
          photos.pp1, photos.pp2, photos.pp3,
  photos.pp4, photos.pp5, photos.pp6,
  photos.pp7, photos.pp8, photos.pp9,
  photos.pp10, photos.pp11, photos.pp12,
  photos.pp13, photos.pp14, photos.pp15,
  photos.pp16, photos.pp17, photos.pp18,
  photos.pp19, photos.pp20, photos.pp21,
  photos.pp22, photos.pp23, photos.pp24,
  photos.pp25, photos.pp26, photos.pp27,
  photos.pp28, photos.pp29, photos.pp30,
  photos.pp31, photos.pp32, photos.pp33,
  photos.pp34, photos.pp35, photos.pp36,
  photos.pp37, photos.pp38, photos.pp39,
  photos.pp40, photos.pp41, photos.pp42,
  photos.pp43, photos.pp44, photos.pp45,
  photos.pp46, photos.pp47, photos.pp48,
  photos.pp49, photos.pp50, photos.pp51,
  photos.pp52, photos.pp53, photos.pp54,
  photos.pp55, photos.pp56, photos.pp57,
  photos.pp58, photos.pp59, photos.pp60,
  photos.pp61, photos.pp62,
  
  
  
          
  
] },
          { label: 'AlbumCover Art', photos: [ photos.albumCoverArjunaOakes2019, photos.albumCoverDJFuckoff2025, photos.albumCoverPhoebeJames,
          photos.aime2024, photos.albumCoverArianeRoy, photos.albumCoverReflexiones,
          ] },
          { label: 'Editorial', photos: [   photos.aime2024, 
              photos.alexa, 
              photos.atallephdreony, 
              photos.britney2024, photos.calissa2019,
  photos.calissaTeiniker2019, photos.calissaPiha1, photos.calissaPiha4copy,
  photos.calissaPiha5, photos.calissaPiha7, photos.calissaPiha8,
  photos.calissaPiha, photos.carole2019, photos.chloe2024,
  photos.claudia2023_1, photos.claudia2023_2, photos.claudia2023_3,
  photos.claudia2023_4, photos.claudia4, photos.claudiaAcrylicTransfer,
  photos.crystal2019,
  photos.dreony2020_1, photos.dreony2020_2,
  photos.hunnyBunny2019, photos.kanePortraits26, photos.imageAssetCopy,
  photos.kane2019, 
  photos.louis2018, photos.louis2019,
  photos.lucaPiscopo2022, photos.luca2022, photos.melissaVanDerAuf, 
  photos.mincaColombia2017, photos.october2019, photos.october2019_2,
  photos.oliviaBrethault1, photos.oliviaBrethault2, photos.oliviaBrethault3,
  photos.oliviaBrethault4, photos.oliviaBrethault5, photos.oliviaBrethault6,
  photos.oliviaBrethault7, photos.outtakeCommissionLivre, photos.secretArnaud, photos.secretCarole,
  photos.secretNoemie, photos.stephenMarr2019, photos.stephenMarr2019_2, photos.thailand2018, 
  photos.vestibule2023_2, photos.vogueItaly, photos.vogueItaly1,
  photos.vogueItaly2,
              
          ] },
          { label: 'Landscapes', photos: [  photos.aotearoa2023,
            photos.hotNCold2023, photos.blueSpring2022, photos.aotearoa2018, photos.mincaColumbia2017,
          ] },
          { label: 'BTS photos', photos: [ photos.renForShortBTS,
          photos.linvincibleBTS1, photos.linvincibleBTS2,
  photos.linvincibleBTS3, photos.linvincibleBTS4, photos.linvincibleBTS5,
  photos.linvincibleBTS6, photos.linvincibleBTS7, photos.linvincibleBTS8,
  photos.linvincibleBTS9, photos.linvincibleBTS10, photos.linvincibleBTS11,

  photos.linvincibleBTS12,

  photos.btsYseult1, photos.btsYseult2, photos.btsYseult3,
  photos.btsPomme, photos.btsSylvain1, photos.btsSylvain2,


          ] },
          { label: 'Publications', photos: [   photos.newBondStreet1, photos.newBondStreet2, photos.newBondStreet3,
  photos.newBondStreet4, photos.newBondStreet5, photos.newBondStreet6,
  photos.newBondStreetPulsemag1, photos.newBondStreetPulsemag2, photos.newBondStreetPulsemag3, photos.bootlegger1, photos.bootlegger2,
  photos.bootlegger3, photos.bootlegger4, photos.bootlegger5,
  photos.bootlegger6, photos.bootlegger7, photos.bootlegger8,
  photos.bootlegger9, photos.bootlegger10, photos.bootlegger11,
  photos.bootlegger12,

  photos.hubertLenoir_interview0, photos.hubertLenoir_interview1,
  photos.hubertLenoir_interview2, photos.hubertLenoir_interview3, photos.hubertLenoir_interview4,
  photos.secretHubert,

  photos.mixmagDJFuckoff1,
  photos.mixmagDJFuckoff2, photos.mixmagDJFuckoff3, photos.mixmagDJFuckoff4,
  photos.mixmagDJFuckoff5, 

  photos.postMagCoverMars2020,



          ] },
        ]
       },
       { name: 'ART', 
  image: ART, type: "photos",
  tabs: [ 
    { label: '2025 Archive', photos: [
    photos.documentationArchives1, photos.documentationArchives2,
  photos.documentationArchives3, photos.documentationArchives4, photos.documentationArchives5,
  photos.documentationArchives6, photos.documentationArchives7, photos.documentationArchives8,
  photos.documentationArchives9,
    ]},
    { label: '2024 - A Sacrificed Body (ASB)', photos: [
      photos.asbDocumentationW1, photos.asbDocumentationAtalleph2,
      photos.asbDocumentationAtalleph3, photos.asbDocumentationAtalleph4,
      photos.asbDocumentationCrucifixion1, photos.asbDocumentationCrucifixion2,
      photos.asbDocumentationCrucifixion4, photos.asbDocumentationHand1,
      photos.asbDocumentationHand2, photos.asbDocumentationKnife1,
      photos.asbDocumentationKnife2, photos.asbDocumentationMarks1,
      photos.asbDocumentationMarks2,
    ]},
    { label: '2021 - VARIATIONS ON OUR FEET UNDER THE TABLE HAPPEN TO BRUSH AGAINST EACH OTHER', photos: [
    photos.variationsOnFeet,
  photos.variationsOnFeet1, photos.variationsOnFeet2,
    ]},
    { label: '2019 - Sculptura', photos: [
    photos.sculptura2, photos.sculptura3, photos.sculptura4,
  photos.sculptura5, photos.sculptura6, photos.sculptura7,
  photos.sculptura8,
    ]},
    { label: '2019 - FEMME FATALE', photos: [
    photos.femmeFatale1, photos.femmeFatale2, photos.femmeFatale3,
    ]},
  ]
}
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

        if (item.type === 'motion') {
        // Show the GIF overlay first
        loadingGif.value = item
        gifDone.value = false
        return
  }

  pushWindow(item)
  }

  function pushWindow(item) {
  openWindows.value.push({
    photos: item.photos ?? null,
    type: item.type ?? null,
    text: item.text ?? null,
    branches: item.branches ?? null,
    id: nextId++,
    name: item.name,
    image: item.image,
    content: item.content ?? [],
    tabs: item.tabs ?? [],
    activeTab: 0,
    activeBranch: 0,
    branchSelected: false,
    focused: true,
    minimized: false,
    maximized: false,
    x: window.innerWidth * 0.5 + Math.random() * window.innerWidth * 0.1 - 300,
    y: window.innerHeight * 0.5 + Math.random() * window.innerHeight * 0.1 - 225,
  })
}

function startGifTimer() {
  setTimeout(() => {
    const item = loadingGif.value
    loadingGif.value = null
    pushWindow(item)
  }, SDTE_DURATION)
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
<div class="openScreen"v-if="!enter">
  <img src="./assets/title.png" width="50%">
  <button  class="enter-button"     v-if="!enter" @click="enter = true">Enter</button>
</div>

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
      

      
    <!-- bio -->
      <div v-if="win.type === 'bio'" class="window-body bio-body">
        <div class="sunken-panel" id="bio" >
          <p>{{ win.text }}</p>  
        </div>
    </div> 

<!-- photos -->

<div v-if="win.type==='photos'" class="window-body">
  <menu role="tablist" class="tablist">
    <li
      v-for="(tab, t) in win.tabs"
      :key="t"
      role="tab"
      :aria-selected="win.activeTab === t"
      @click="win.activeTab = t"
    >
      <a>{{ tab.label }}</a>
    </li>
  </menu>
  <div class="sunken-panel" >
        <div id="photoWrapper">
              <div v-for="photo in win.tabs[win.activeTab].photos"
                :key="photo"
                class="photoItem"
              >
                <img :src= "photo"  class="imgCrop">
              </div>
        </div>

  </div>
</div>



    <!-- motion -->
      <div v-else-if="win.type==='motion'" class="window-body">
            <menu role="tablist" v-if="win.branches">
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


            <template v-if="win.branches">
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

            </template>



      </div>
  
</div>
<footer class="window footer-window">
  <div class="dropdown-wrapper">
    <button @click="dropdownOpen = !dropdownOpen">Menu</button>
    <div v-if="dropdownOpen" class="dropdown">
      <div
        v-for="item in icons"
        :key="item.name"
        class="dropdown-item"
        @click="openWindow(item); dropdownOpen = false"
      >
        <img :src="item.image" :alt="item.name" />
        <span>{{ item.name }}</span>
      </div>
    </div>
  </div>
</footer>

 

</div>

<div v-if="loadingGif" class="gif-overlay">
  <img :src="SDTE" @load="startGifTimer" />
</div>
</template>

<style scoped>

.dropdown-wrapper {
  position: relative;
}

.dropdown {
  position: absolute;
  bottom: 100%;
  left: 0;
  background: silver;
  border: 2px solid white;
  z-index: 200;
  min-width: 160px;
}

.dropdown-item {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 8px;
  padding: 6px 10px;
  cursor: pointer;
}

.dropdown-item:hover {
  background: #4f5070;
  color: white;
}

.dropdown-item img {
  width: 24px;
  height: 24px;
  image-rendering: pixelated;
}

.gif-overlay {
  position: fixed;
  inset: 0;
  z-index: 999;
  display: flex;
  align-items: center;
  justify-content: center;
  background: black;
}

@keyframes gifWait {
  from { opacity: 1; }
  to   { opacity: 1; }
}

.gif-overlay img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

#photoWrapper {
  display: block !important;
  columns: 3;
  column-gap: 6px;
  height: auto !important;
  flex: 1;              /* ← replaces height: 100% */
  min-height: 0;
}

.photoItem {
  break-inside: avoid;
  margin-bottom: 6px;
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
}

.photoItem img {
  width: 100%;   /* stretches to fill the column */
  height: auto;  /* lets the natural aspect ratio breathe */
  display: block;
  border-radius: 10px!important;
  object-fit: cover;
  display: block;
}

#bio {
  background-color: white;
  width: 100%!important;
  height: 100%!important;
}

.bio-body {
  font-weight: 800;
  margin-top: 50px;
  padding: 10px;

}

#bio p {
  margin: 20px;
  font-size: 22px;
}

.openScreen {
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  height: 100vh;
  width: 100vw;
  
}

.openScreen img {
  margin-top: 40vh;
}

menu {
  display: flex;
 flex-direction: row;
 align-content: center;
  width: 100%;
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
  display: flex;
  flex-direction: column;
  height:100%;
  min-height: 0; 
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
  overflow: hidden;
  flex-shrink: 0;
}

.crop img {
  width: 100%;
  border-radius: 10px;
  aspect-ratio: 16/9;

  object-fit: cover;
  display: block;
}

.imgCrop {
  width: 100%;
  border-radius: 10px;
  object-fit: cover;
  display: block;
}


.window-body img{
  padding: 3px;

  
}

.window .title-bar {
  color: azure;
  font-weight: 900;
}

.window .title-bar span{
  width: 100%;
  text-align: left;

}

.window .title-bar  {
  background: #4f5070 ;
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
  width: 100vw;
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
  align-items: start;
  width: 100%;
  overflow: visible;

}

.enter-button {
  z-index: 100;
  cursor: pointer;
}
</style>
