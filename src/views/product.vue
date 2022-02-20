<template>
  <v-container>
    <center><h1>HUNTER SHOP</h1></center>
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto mb-12"
        max-width="500"
        v-for="(i, index) in productlist"
        :key="index"
      >
        <v-img class="white--text align-end" height="500px" :src="i.imageurl">
        </v-img>
        
        <v-card-text class="text--primary">
          <div><h2>{{ i.prodText }}</h2></div>
        </v-card-text>

        <v-card-subtitle class="textscale"><h1 class="fontcolor">{{ i.priceText }}</h1></v-card-subtitle>

        <v-card-actions>
          <v-btn color="info" text :to="'/detail/' + i.id">detail</v-btn>
          <v-btn color="orange" text @click="selected(i)"> Add </v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
    <v-container
      ><h4>Total Amount : {{ total() }} €</h4></v-container
    >
    <v-container grid-list-xs class="dark">
      <router-view :key="$route.path"></router-view>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          id:"Item ID: 1068027",
          imageurl:
            "https://store.capcom-europe.com/media/image/b0/c6/13/1068027_Monster_Hunter_Wind_Serpent_Ibushi_600x600.webp",
          priceText: "Price : 30 €",
          prodText: 'Monster Hunter Rise Chibi Plush "Wind Serpent Ibushi"',
          active: false,
          price: 30,
        },

        {
          id:"Item ID: 1068028",
          imageurl:
            "https://store.capcom-europe.com/media/image/81/0c/9b/1068028_Monster_Hunter_Thunder_Serpent_Narwa_600x600.webp",
          priceText: "Price : 30 €",
          prodText: 'Monster Hunter Rise Chibi Plush "Thunder Serpent Narwa"',
          active: false,
          price: 30,
        },

        {
          id:"Item ID: 1070799",
          imageurl:
            "https://store.capcom-europe.com/media/image/1a/ee/88/1070799-monster-hunter-statue-palamute-creators-model-5_600x600.webp",
          priceText: "Price : 190 €",
          prodText: "Monster Hunter Statue Palamute Creator's Model",
          active: false,
          price: 190,
        },

        {
          id:"Item ID: 1078702",
          imageurl:
            "https://store.capcom-europe.com/media/image/41/83/28/1078702-monster-hunter-statue-creators-model-rathian-front_600x600.webp",
          priceText: "Price : 140 €",
          prodText: "Monster Hunter Statue Rathian Creator's Model",
          active: false,
          price: 140,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
.textscale{
  margin-top: 1px;
}
.fontcolor{
  font-weight: 1000;
}
</style>
