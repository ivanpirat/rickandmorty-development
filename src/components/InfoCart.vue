<template >
 
    <div @mousemove="cursortrek" @mouseup.stop
      class="infocart"
      ref="divA"
      @click="clickInfocart"
      :style="{
        left: xt + 'px',
        top: yt + 'px',
      }"
    >
      <div class="close" @mouseup="closeWindow">❌</div>
      <div class="pers">
        <img :src="srs" :alt="name" />
        <div class="persimfo">
          <h2>Имя: {{ name }}</h2>
          <h2>Gender: {{ gender }}</h2>
          <h2>Раса: {{ species }}</h2>
          <h2>На даный момент: {{ status }}</h2>
        </div>
      </div>
      <div class="pers2">
        <h2>Местоположение: {{ location }}</h2>
      </div>
    </div>
 
</template>

<script>
export default {
  functional: true,
  props: ["pers"],
  emits: ["close-window"],
  data() {
    return {
      ww:window.innerWidth,
      mouse: false,
      name: this.pers.name,
      gender: this.pers.gender,
      species: this.pers.species,
      status: this.pers.status,
      srs: this.pers.image,
      location: this.pers.location.name,
      x: 0,
      y: 0,
      xt: 0,
      yt: 0,
    };
  },
  mounted() {
    this.xt = window.innerWidth / 2;
    this.yt = window.innerHeight / 2;
  },
  methods: {
    closeWindow() {
      this.$emit("close-window");
    },
    clickInfocart(e) {
      const x = this.xt - this.x;
      const y = this.yt - this.y;
      this.x = x - e.x - 15;
      this.y = y - e.y - 15;
      this.mouse = !this.mouse;
    },
    cursortrek(e) {
      if (this.mouse && this.ww > 700) {
        this.xt = e.x + this.x;
        this.yt = e.y + this.y;
      }
    },
  },
};
</script>

<style scoped>
.stop {
  position: absolute;
  background-color: red;
}
.pers {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  height: 50%;
}
.persimfo {
  font-size: 12px;
  padding: 15px;
  outline: none;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: space-around;
  cursor: move;
}

.infocart {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  display: flex;
  flex-direction: column;
  position: fixed;
  outline: none;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 600px;
  background-color: rgb(255, 255, 255);
  box-shadow: rgba(0, 0, 0, 0.226) 0 0 22px;
  border-radius: 15px;
  overflow: hidden;
-webkit-user-select: none;
-khtml-user-select: none;
-moz-user-select: none;
-ms-user-select: none;
user-select: none;
}
h2 {
  font-size: 22px;
}
.close {
  position: fixed;
  left: 95%;
  top: 5%;
  font-size: 22px;
  cursor: pointer;
  padding: 5px;
  transform: translate(-50%, -50%);
}
img {
  height: 90%;
  padding: 10px;
  border-radius: 30px;
}

@media screen and (max-width: 800px) {
  .pers {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 70%;
  }
  img {
    height: none;
    width: 100%;
    padding: 0;
    border-radius: 0;
  }

  .persimfo {
    font-size: 8px;
    padding: 0;
    align-items: center;
  }
  .infocart {
    width: 80%;
    top: 50%;
    transform: translate(-50%, -50%);
  }
  h2 {
  font-size: 16px;
}
  .close {
    position: fixed;
    left: 95%;
    top: 3%;
    transform: translate(-50%, -50%);
  }
}
</style>