<template>
  <div>
    <img class="weapon-img" :alt="`${weaponName}`" :src="require(`~/assets/Weapons/${weaponImg}`)" />
    <aspect v-bind:weaponIndex="weaponIndex" v-bind:aspectIndex="aspectIndex"></aspect>
    <p>{{weaponName}}</p>
<!--    <b-button size="sm" v-on:click="randomize(); ">randomize</b-button>-->
  </div>
</template>

<script>
import hades from '~/assets/data.json';
import {getRandomInt} from "~/assets/helper.js";
import Aspect from "~/components/Aspect";

export default {
  name: "Weapon",
  components: {Aspect},
  props: {
    weaponIndex: Number,
    aspectIndex: Number
  },
  data () {
    return {
      weaponIndex: this.weaponIndex,
      aspectIndex: this.aspectIndex,
      weaponImg: hades.Weapons[this.weaponIndex].img,
      weaponName: hades.Weapons[this.weaponIndex].name
    }
  },
  methods : {
    randomize : function (event) {
      let i = getRandomInt(0, hades.Weapons.length)
      let weapon = hades.Weapons[i];
      this.image = weapon.img;
      this.alt_text = weapon.name + ", "  + weapon.alt_name;
      //alert(`${hades.Weapons[this.i].name}`);
    },
    setWeapon : function (index) {
      let weapon = hades.Weapons[index];
      this.image = weapon.img;
      this.alt_text = weapon.name + ", "  + weapon.alt_name;
    },
  }
}
</script>

<style scoped>
.weapon-img {
  height: 416px;
  width: 288px;
  object-fit: none;
  display: inline-block;
}
</style>
