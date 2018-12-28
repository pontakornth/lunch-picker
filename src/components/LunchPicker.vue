<template>
<div>
  <p>เลือกประเภทอาหาร</p>
  <v-form lazy-validation>
    <v-checkbox
     label="ไก่"
     v-model="catagories" value="ไก่" :rules="[validate_menus]"
    />
    <v-checkbox
     label="หมู"
     v-model="catagories" value="หมู" :rules="[validate_menus]"/>
     <v-checkbox
     label="กุ้ง"
     v-model="catagories" value="กุ้ง" :rules="[validate_menus]"/>
     <v-btn @click="randomPick" color="primary">สุ่ม</v-btn>
  </v-form>
  <h3 v-if="this.isPicked">{{this.pickedMenus}}</h3>
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
    }
  },
  methods: {
    randomPick() {
      let selections = []
      this.catagories.forEach(catagory => {
        selections.push(foods[catagory])
      })
      selections = flatten(selections)
      this.pickedMenus = sample(selections)
      this.isPicked= !(this.isPicked)
    },
    validate_menus() {
      return this.catagories.length > 0 ? true : "เลือกอย่างน้อย 1 อย่าง"
    }
  },

}
</script>

<style>

</style>
