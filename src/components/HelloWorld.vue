<template>
<div class="range_div">
    <input
    type="range"
    class="range"
    name=""
    id=""
    min="1"
    max="300"
    step="1"
    v-model="valueRange"
  />
</div>

  <div class="collectoinCart" v-if="valueRange > 1">
    <Cart
      v-for="(item, index) in arrinfomod"
      :key="index"
      :arrItemsApi="item"
    />
  </div>
  <h1 v-else>увеличьте ползунок</h1>
</template>

<script>
import Cart from "./Cart";

export default {
  name: "HelloWorld",
  components: {
    Cart,
  },
  watch: {
    valueRange(value) {
      this.valueRangeall(value);
      console.log(value);
    },
  },
  data() {
    return {
      arrinfo: [],
      arrinfomod: [],
      valueRange: 0,
    };
  },
  mounted() {
    this.allApiItem();
    console.log(this.arrinfo);
  },
  methods: {
    valueRangeall(id) {
      this.arrinfomod.length = 0;
      this.arrinfomod = this.arrinfo.filter((item) => item.id < id);
    },

    Apiitem(id) {
      fetch("https://rickandmortyapi.com/api/character/" + id, {
        method: "GET",
      })
        .then((resp) => resp.json())
        .then((res) => {
          this.arrinfo.push(res);
        });
    },
    allApiItem() {
      for (let i = 1; i < 301; i++) {
        this.Apiitem(i);
      }
    },
  },
  computed: {},
};
</script>
<style   scoped>
.range {
  width: 90%;
  height: 30px;
  
}
.range_div{
padding: 10px;
  background-color: rgb(31, 53, 82);
  margin: 2%;
  border-radius: 20px;
}
.collectoinCart {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}
</style>