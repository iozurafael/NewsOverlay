<template>
  <v-app style="background: none">
    <v-main>
      <router-view :newsPage="newsPage" :talkingStage="talkingStage" />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    // Tot ce ţine de pagina de News
    newsPage: {
      headerText: "MUIE MA SALAM", // Textul ce apare ca header pe burtiera
      liveText: "LIVE MUIE MUIE MUIE", // Textul ce va fi afişat pe slot-ul din stânga sus. Deobicei este "LIVE"
      bottomTexts: [
        // Textele ce se vor afisa in partea de jos a paginii. Poti adauga cate vrei.
        { text: "Salut si bine v-am gasit" },
        { text: "Sa va iau in sabie ba terminatilor care sunteti terminati" },
        { text: "Alooooooooooooooooo mi-e foame da-mi si mie 100 euro" },
        { text: "Cf test tu bn eu?" },
        { text: "OK DAR CINE A INTREBAT" },
      ],
    },
    talkingStage: {
      people: [
        { text: "twitter.com/rafael" },
        { text: "twitter.com/este" },
        { text: "twitter.com/seful" },
        { text: "twitter.com/la bani" },
        { text: "twitter.com/la bani" },
        { text: "twitter.com/la bani" },
        { text: "twitter.com/la bani" },
      ],
    },
  }),
};
</script>

<style>
.OverlayPage {
  height: 100vh;
}

::-webkit-scrollbar {
  width: 0px !important;
}
</style>
