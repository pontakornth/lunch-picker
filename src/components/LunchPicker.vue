<template>
<div>
  <p>เลือกประเภทอาหาร</p>
  <v-form lazy-validation>
     <v-checkbox v-for="c in Object.keys(this.availableCatagories)" :key="c" v-model="catagories" :value="c" :rules="[validate_menus]" :label="c"/>
     <v-btn @click="randomPick" color="primary">สุ่ม</v-btn>
  </v-form>
  <h3 v-if="this.catagories.length > 0">{{this.pickedMenus}}</h3>
</div>
</template>

<script>
import {flatten, sample} from 'lodash'
import foods from '../foods.json'
export default {
  data() {
    return {
      catagories: [],
      pickedMenus: "",
      menus: [],
      isPicked: false,
      availableCatagories: foods
    }
  },
  methods: {
    randomPick() {
      this.pickedMenus = "รอสักครู่"
      let selections = []
      this.catagories.forEach(catagory => {
        selections.push(foods[catagory])
      })
      selections = flatten(selections)
      setTimeout(() => {this.pickedMenus = sample(selections)},500)
      
      //this.isPicked= !(this.isPicked)
    },
    validate_menus() {
      return this.catagories.length > 0 ? true : "เลือกอย่างน้อย 1 อย่าง"
    }
  },

}
</script>

<style>

</style>
