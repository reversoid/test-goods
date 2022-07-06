<template>
  <div class="wrapper">
    <h1 class="mega-title">Добавление товара</h1>
    <section class="mainpage">
      <ControlBar style="margin-right: 1rem;" :_createProduct="createProduct"/>
      <GoodsList :products="goods" :deleteCallback="deleteProduct" />
    </section>
  </div>
</template>

<script>
import GoodsList from "./components/GoodsList.vue";
import ControlBar from "./components/ControlBar.vue";

let id = 0;
export default {
  name: "App",
  components: {
    GoodsList,
    ControlBar,
  },
  data() {
    return {
      goods: [{ id: id++, title: 'Название', description: 'Описание товара... описание...', price: 9000, imgLink: 'https://avatars.mds.yandex.net/get-mpic/4249638/img_id6129126127483725327.jpeg/orig' }],
    }
  },
  methods: {
    deleteProduct(id) {
      this.goods = this.goods.filter((product) => product.id != id);
    },
    createProduct(imgLink, title, description, price) {
      this.goods.push({title, description, price, imgLink, id: ++id})
    }
  }
};
</script>

<style lang="scss">
@import "./styles/reset";
@import "./styles/shared";

.mainpage {
  display: flex;
}

.mega-title {
  font-size: 1.75rem;
  margin-bottom: 1rem;
  font-weight: 600;
}
</style>
