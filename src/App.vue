<template>
  <!-- area -->
  <div>
    <p>choice area</p>
  <label for="area">area: </label>
  <select v-model="selected" @change="fetchTags">
    <option v-for="area in area" :value="area.id" :key="area.id">
      {{ area.name }}
    </option>
  </select>
  <br>
  <!-- prefecture -->
  <div v-if="selected">
    <label for="tag">town: </label>
    <select name="tag" v-model="selectedTag">
      <option v-for="tag in tags" :value="tag.name" :key="tag.id">
        {{ tag.name }}
      </option>
      </select>
  </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        selected: '',
        selectedTag: '',
        area: [
          { id: 1, name: 'Hokkaido' },
          { id: 2, name: 'Tokyo' },
          { id: 3, name: 'Osaka' }
        ],
        tags: [],
      }
    },
   methods: {
      fetchTags: function() {
      var tmp_tags = [];
      if (this.selected == 1) {
        tmp_tags = [
          {id: 6, name: "Sapporo"},
          {id: 7, name: "Aasahikawa"}
        ];
      } else
        if(this.selected == 2) {
        tmp_tags = [
          {id: 8, name: "Oota-ku"},
          {id: 9, name: "Chiyoda-ku"}
        ];
      } else
        if(this.selected == 3) {
        tmp_tags = [
          {id: 8, name: "Osaka"},
          {id: 9, name: "Neyagawa"}
        ];
      } else {
        alert('Invalid value!!');
      }
      
      this.tags = tmp_tags;
    }
  }
}

</script>