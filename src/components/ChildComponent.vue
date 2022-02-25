<template>
  <div id="child">
    <h2>Child Component</h2>
    <p>
      Parent Favourite Fruit is <span id="fruit"> {{ favFruit }}</span>
    </p>
    <p>
      Favourite Dish
      <input type="text" v-model="childFavDish" />
      <button @click="sendData2Parent">Send data 2 parent</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "ChildComponent",
  props: ["favFruit"],
  data() {
    return {
      childFavDish: "",
    };
  },
  methods: {
    sendData2Parent() {
    //   this.$emit("dishEvent", {
    //     dish: this.childFavDish,
    //     n1: 10,
    //     n2: 20,
    //   });
    // this.$emit("dishEvent", [this.childFavDish, 10, 20]);
    this.$emit("dishEvent", this.childFavDish);
    },
  },
};
</script>

<style>
#child {
  border: 2px solid blue;
  margin: 5px;
  padding: 5px;
}
#fruit {
  font-weight: bold;
}
</style>