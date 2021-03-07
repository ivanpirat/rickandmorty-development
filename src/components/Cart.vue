<template>
  <div class="cart" @click.stop="hiddenBloc=true">
    <img :src="srtimg" alt="title" />
    <h3>
      Имя: <strong>{{ name }}</strong>
    </h3>
  </div>
    <InfoCart  :pers='arrItemsApi' 
    v-if="hiddenBloc"
    @close-window='hiddenBloc=false'  />
</template>

<script>
import InfoCart from "./InfoCart";
export default {
  components: {
    InfoCart,
  },
  data() {
    return {
      name: this.arrItemsApi.name,
      srtimg: this.arrItemsApi.image,
      hiddenBloc:false,
    };
  },
  props: ["arrItemsApi"],
};
</script>

<style  scoped>
.cart {
   font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
   cursor: pointer;
  display: flex;
  flex-direction: column;
  width: 200px;
  margin: 10px;
  box-shadow: rgba(0, 0, 0, 0.226) 0 0 22px;
  border-radius: 15px;
  overflow: hidden;
}
img {
  width: 100%;
}
@media screen and (max-width: 800px) {
  .cart {
    width: 300px;
  }
}
</style>