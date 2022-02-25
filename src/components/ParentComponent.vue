<template>
  <div id="parent">
    <h2>Parent Component</h2>
    <p>
      Favourite Fruit
      <input type="text" v-model="parentFavFruit" />
      <button @click="sendData2Child">Send data to child</button>
    </p>
    <p>
        Child Favourite Dish is <span id="dish">{{ childFavDish }}</span>
    </p>
    <ChildComponent
      :fav-fruit="dataForChild"
      @dish-event="handleDishEvent($event)"
    />
  </div>
</template>

<script>
import ChildComponent from "./ChildComponent.vue";

export default {
  name: "ParentComponent",
  components: {
    ChildComponent,
  },
  data() {
    return {
      parentFavFruit: "",
      dataForChild: "",
      childFavDish: '',
    };
  },
  methods: {
    sendData2Child() {
      this.dataForChild = this.parentFavFruit;
    },
    handleDishEvent(event) {
        console.log(event);
        this.childFavDish = event;
    }
  },
};
</script>

<style>
#parent {
  border: 2px solid red;
  margin: 5px;
  padding: 5px;
}

#dish {
    font-weight: bold;
}
</style>