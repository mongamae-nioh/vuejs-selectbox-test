<template>
  <!-- area -->
  <div>
    <p>Choose your area</p>
  <label for="area">area: </label>
  <select v-model="selectedArea" @change="fetchAreas">
    <option v-for="area in area" :value="area.id" :key="area.id">
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
  <div v-if="selectedPref">
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
  <div v-if="selectedCity">
    <button type=button>button</button>
  </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        selectedArea: '',
        selectedPref: '',
        selectedCity: '',
        area: [
          { id: 1, name: 'Hokkaido, Tohoku' },
          { id: 2, name: 'Kanto' },
          { id: 3, name: 'kansai' }
        ],
        prefectures: [],
        cities: [],
      }
    },
   methods: {
      fetchAreas: function() {
      var pref_tags = [];
      if (this.selectedArea == 1) {
        pref_tags = [
          {id: 101, name: "Hokkaido"},
        ];
      } else
        if(this.selectedArea == 2) {
        pref_tags = [
          {id: 102, name: "Ibaraki"},
          {id: 103, name: "Tokyo"}
        ];
      } else
        if(this.selectedArea == 3) {
        pref_tags = [
          {id: 104, name: "Osaka"},
          {id: 105, name: "Kobe"}
        ];
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