<template>
  <div id="app">
    <v-container>
      <v-row>
        <v-col
          v-for="(photo, idx) in photos"
          :key="idx"
          cols="12"
          sm="12"
          md="12"
          lg="6"
          xl="6"
        >
          <v-card
            class="instaxPhotoContainer"
            v-bind:style="{ transform: `rotate(${photo.rot})` }"
            v-bind:href="photo.link"
          >
            <img class="instaxPhoto" :src="photo.img" />
            <span class="instaxPhotoTitle">{{ photo.name }}</span>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    photos: [
      {
        name: "Portfolio Site",
        img: require("@/assets/imgs/portfolio.png"),
        link: "https://portfolio.morio.dev/",
        rot: "-3deg",
      },
      {
        name: "Blog",
        img: require("@/assets/imgs/blog.png"),
        link: "https://blog.morio.dev/",
        rot: "4deg",
      },
    ],
  }),
};
</script>

<style lang="scss">
html {
  background-image: url("assets/imgs/bg.png");
  background-size: auto 100vh;
  background-repeat: repeat;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-left: 20vw;
  margin-right: 15vw;
  margin-top: 30vh;
  margin-bottom: 10vh;
  @media only screen and (max-width: 1264px) {
    margin-left: 10vw;
    margin-right: 8vw;
    margin-top: 5vh;
  }
}

.instaxPhotoContainer {
  width: 90%;
  filter: grayscale(100%);
  transition: 0.5s;
  background-color: #eeeeee;
  margin: 5%;
  padding-top: 5%;
  padding-bottom: 3%;
  &:hover {
    filter: none;
    box-shadow: 0 16px 80px -24px red !important;
    transition: 0.5s;
  }
}

.instaxPhoto {
  width: 90%;
  border: 1px solid #55555555;
  margin-bottom: 3%;
}

.instaxPhotoTitle {
  font-family: "Courier New", Courier, "American Typewriter", monospace;
  font-weight: 600;
  color: #dd1111;
  font-size: 36px;
  @media only screen and (max-width: 960px) {
    font-size: 30px;
  }
  @media only screen and (max-width: 600px) {
    font-size: 24px;
  }
}
</style>
