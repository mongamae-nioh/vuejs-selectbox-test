<template>
  <!-- area -->
  <div>
    <p>Choose your area</p>
  <label for="area">area: </label>
  <select v-model="selectedArea" @change="fetchAreas">
    <option v-for="area in areas" :value="area.id" :key="area.id">
      {{ area.name }}
    </option>
  </select>
  <br>
  <!-- prefecture -->
  <div v-if="selectedArea">
    <p>Choose your prefectures</p>
    <label for="prefecture">prefecture: </label>
    <select name="prefecture" v-model="selectedPref" @change="fetchCities">
      <option v-for="prefecture in prefectures" :value="prefecture.id" :key="prefecture.id">
        {{ prefecture.name }}
      </option>
      </select>
  </div>
  <!-- city -->
  <div v-if="selectedPref > 0">
    <p>Choose your city</p>
    <label for="city">city: </label>
    <select name="city" v-model="selectedCity">
      <option v-for="city in cities" :value="city.id" :key="city.id">
        {{ city.name }}
      </option>
      </select>
  </div>
  <br>
  <!-- button -->
  <div v-if="selectedCity > 0">
    <button type=button>button</button>
  </div>
  </div>
</template>

<script>
import areas from "./static/area.json"
import hokkaido from "./static/hokkaido.json"
import kanto from "./static/kanto.json"
import kansai from "./static/kansai.json"
  export default {
    data() {
      return {
        selectedArea: '',
        selectedPref: '',
        selectedCity: '',
        areas: areas,
//        prefectures: prefectures,
        prefectures: [],
        cities: [],
      }
    },
   methods: {
      fetchAreas: function() {
      var pref_tags = [];
      if (this.selectedArea == 1) {
        pref_tags = hokkaido
      } else
        if(this.selectedArea == 3) {
        pref_tags = kanto;
      } else
        if(this.selectedArea == 5) {
        pref_tags = kansai;
      } else {
        alert('Invalid value!!');
      }
      
      this.prefectures = pref_tags;
    },
      fetchCities: function() {
      var city_tags = [];
      if (this.selectedPref == 101) {
        city_tags = [
          {id: 1001, name: "Sapporo"},
        ];
      } else
        if(this.selectedPref == 102) {
        city_tags = [
          {id: 1002, name: "Mito"},
        ];
      } else
        if(this.selectedPref == 103) {
        city_tags = [
          {id: 1004, name: "Chiyoda-ku"},
          {id: 1005, name: "Kita-ku"}
        ];
      } else {
        alert('Invalid value!!');
      }
      
      this.cities = city_tags;
    }

}
}

</script>