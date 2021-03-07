<template>
  <div class="stop" @mousemove="cursortrek">
    <div
      class="infocart"
      ref="divA"
      @mouseup="clickInfocart"
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
  </div>
</template>

<script>
export default {
  props: ["pers"],
  emits: ["close-window"],
  data() {
    return {
      mouse: false,
      name: this.pers.name,
      gender: this.pers.gender,
      species: this.pers.species,
      status: this.pers.status,
      srs: this.pers.image,
      location : this.pers.location.name,
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
      if (this.mouse && window.innerWidth > 700) {
        this.xt = e.x + this.x;
        this.yt = e.y + this.y;
      }
    },
  },
};
</script>

<style scoped>
.stop {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  width: 100vw;
  height: 100vh;
  position: fixed;
  transform: translate(-50%, -50%);
  left: 50%;
  top: 50%;
  background-color: rgba(0, 0, 0, 0.747);
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
  display: flex;
  flex-direction: column;
  position: fixed;
  outline: none;
  left: 50%;
  top:50% ;
  transform: translate(-50%, -50%);
  width: 600px;
  background-color: rgb(255, 255, 255);
  box-shadow: rgba(0, 0, 0, 0.226) 0 0 22px;
  border-radius: 15px;
  overflow: hidden;
}
h2
{
    font-size: 22px;
}
.close {
  position: fixed;
  left: 97%;
  top: 2%;
  font-size: 22px;
  cursor: pointer;
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
    font-size: 12px;
      padding: 0;
    align-items: center;
  }
  .infocart {
    width: 80%;
    top: 50%;
    transform: translate(-50%, -50%);
  }
  .close {
    position: fixed;
    left: 95%;
    top: 3%;
    transform: translate(-50%, -50%);
  }
}
</style>