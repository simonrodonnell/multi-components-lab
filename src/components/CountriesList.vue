<template lang="html">
  <div class="">
    <label>Select country:</label>
    <select @change="handleChange" v-model="selectedCountry">
      <option v-for="(country, index) in countries" :value="country" :key="index">{{ country.name }}</option>
    </select>
    <ul>
    <!-- <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item> -->
  </ul>
</div>
</template>



<script>
import ListItem from "./ListItem.vue";
import {eventBus} from "../main.js";
export default {
  data(){
    return {
      selectedCountry: null
    }
  },
  name: "countries-list",
  props: ["countries", "country"],
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  },
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
</style>
