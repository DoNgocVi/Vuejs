<template>
  <div class="home">
    <div class="container">
      <div class="row">
        <div class="col-md-6 offset-md-3">
          <ul class="list-group">
            <li
              v-for="city in cities"
              :key="city.id"
              class="
                list-group-item
                d-flex
                justify-content-between
                align-items-center
              "
            >
              <span class="city">{{ city.name }}</span>
              <span class="country">{{ city.country }}</span>
              
              <span class="badge badge-primary badge-pill">
                <router-link
                  :to="{ path: `/cities/${city.id}` }"
                  class="btn btn-primary ml-2"
                  >Edit</router-link
                >
                <a href="#" class="btn btn-danger" @click="deleteCity(city.id)">
                  Delete
                </a>
              </span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
import citiesColRef from "../firebase";
import { deleteDoc, doc } from "firebase/firestore";

export default {
  computed: {
    ...mapState(["cities"]),
  },
  methods: {
    ...mapActions(["fetchCities"]),
    async deleteCity(cityId) {
      let cityRef = doc(citiesColRef, cityId);
      await deleteDoc(cityRef);
      this.$router.go();
    },
  },
  created() {
    this.fetchCities("createCity");
  },
};
</script>

<style scoped>
  .city{
    width: 150px;
    text-align: start;
  }
  .country{
    width: 70px;
    text-align: start;
  }
</style>