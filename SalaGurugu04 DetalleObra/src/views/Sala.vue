<template>
  <Navbar />
  <div class="row justify-content-center">
    <BaseTarjeta
      class="col-4 m-2"
      v-for="obra in obras"
      :key="obra.id"
      :obra="obra"
    />
  </div>
  <div class="d-flex justify-content-center">
    <Pagination/>
  </div>
</template>

<script>
import Navbar from "../components/Navbar.vue";
import BaseTarjeta from "../components/BaseTarjeta.vue";
import Pagination from "../components/Pagination.vue";
import { collection, getDocs, query, orderBy, limit, startAfter } from "firebase/firestore";
import { db } from "../main";
export default {
  name: "Sala",
  props: ['page'],
  components: {
    Navbar,
    BaseTarjeta,
    Pagination,
  },
  data() {
    return {
      lastVisible: "",
      obras: [],
      obra: {
        title: "",
        author: "",
        date: "",
        photo: "",
      },
    };
  },
  methods: {
    async obtenerDatos() {
     
      const q = query(
        collection(db, "obras"),
        orderBy("date")
      );

      const querySnapshot = await getDocs(q);
      querySnapshot.forEach((doc) => {
        let obra = doc.data();
        obra.id = doc.id;
        this.obras.push(obra);
      });
    },
  },
  mounted() {
    this.obtenerDatos();
  },
};
</script>

<style>
.text-center {
  text-align: center;
}
</style>
