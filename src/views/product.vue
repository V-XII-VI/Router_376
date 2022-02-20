<template>
  <v-container>
    <center><h1>Flower Shop</h1></center>
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto mb-12"
        max-width="800"
        v-for="(i, index) in productlist"
        :key="index"
      >
        <v-img class="white--text align-end" height="800px" :src="i.imageurl">
        </v-img>

        <v-card-text class="text--primary">
          <div>
            <h2>{{ i.prodText }}</h2>
          </div>
        </v-card-text>

        <v-card-subtitle class="textscale"
          ><h1 class="fontcolor">{{ i.priceText }}</h1></v-card-subtitle
        >

        <v-card-actions>
          <v-btn color="info" text :to="'/detail/' + i.id">detail</v-btn>
          <v-btn color="orange" text @click="selected(i)"> Add </v-btn>
        </v-card-actions>
      </v-card>
    </v-container>
    <v-container
      ><h4>รวมราคาทั้งหมด : {{ total() }} บาท</h4></v-container
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
          id: '-ดอกลิลลี่สีขาว ตัวแทนของ "ความบริสุทธิ์ใจ, ความไร้เดียงสา, ความอ่อนน้อมถ่อมตน"',
          imageurl: "https://img.kapook.com/u/2019/jutharat/w1/z36_4.jpg",
          priceText: "ราคา : 20 บาท",
          prodText: "ดอกลิลลี่สีขาว",
          active: false,
          price: 20,
        },

        {
          id: 'เป็นดอกไม้ที่บอกเป็นนัยว่า "ขอเป็นชู้ทางใจ" หรือ หมายถึงความสุข สนุกสนาน ร่าเริง',
          imageurl:
            "https://s.isanook.com/hm/0/ud/0/3133/istock_000007428513_small.jpg",
          priceText: "ราคา : 20 บาท",
          prodText: "ดอกกุหลาบสีเหลือง",
          active: false,
          price: 20,
        },

        {
          id: "ในด้านความรัก ดอกทานตะวันนั้นสื่อถึงความรักบริสุทธิ์และมั่นคง เหมือนกับไคลทีที่เฝ้ามองเทพอพอลโลไม่ไปไหน ดังนั้นการเรามอบดอกทานตะวันให้ใครจึงหมายถึงการที่เราบอกผู้รับว่า ความรักของฉันที่มีให้เธอจะมั่นคง ไม่เปลี่ยนแปลง เหมือนที่ดอกทานตะวันเฝ้ามองดวงอาทิตย์เสมอไป และนอกจากความหมายซึ้ง ๆ แบบนี้แล้ว ดอกทานตะวันยังใช้สื่อถึงความร่าเริงสดใสและความสุข เหมาะสำหรับมอบให้เป็นของขวัญเพื่ออวยพรให้ผู้รับมีแต่ความสุขและความสดใส",
          imageurl:
            "https://www.ikea.com/th/th/images/products/smycka-artificial-flower-sunflower-yellow__0797554_pe767321_s5.jpg?f=s",
          priceText: "ราคา : 20 บาท",
          prodText: "ดอกทานตะวัน",
          active: false,
          price: 20,
        },

        {
          id: "เป็นดอกไม้แห่งคำมั่นสัญญา ความรักความผูกพัน",
          imageurl:
            "https://acsst.files.wordpress.com/2019/01/50553648_2122929084490478_542354017573928960_n.jpg",
          priceText: "ราคา : 20 บาท",
          prodText: "แกลดิโอลัส",
          active: false,
          price: 20,
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
.textscale {
  margin-top: 1px;
}
.fontcolor {
  font-weight: 1000;
}
</style>
