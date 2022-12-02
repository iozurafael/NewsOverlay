<template>
  <div class="OverlayPage d-flex flex-column">
    <v-row style="padding: 2vh; margin: 0" justify="space-around" class="row">
      <v-col
        cols="6"
        v-for="(item, index) in talkingStage.people"
        :key="index"
        class="d-flex flex-column pa-2 coxl"
      >
        <div class="webcam"></div>
        <div class="invite-name">{{ item.text }}</div>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  props: ["talkingStage"],
  name: "TalkingStage",
  components: {},
  data() {
    return {};
  },

  beforeDestroy() {},
  created() {},
};
</script>

<style>
.webcam {
  height: 100%;
  /* border-image: linear-gradient(red, purple) 30; */
  border-width: 0.4rem;
  border-style: solid;
  background-color: green;
  border-color: #fd243c;
}

.invite-name {
  min-height: 1rem;
  background-color: #fd243c;
  color: white;
  font-weight: 800;
  width: fit-content;
  text-align: center;
  padding: 0.2rem 0.4rem 0 0.4rem;
  text-transform: uppercase;
  /* margin-left: auto; */
}
.coxl:nth-child(even) .invite-name {
  margin-left: auto;
}
</style>
