<template>
  <div>
    <img :alt="`${alt_text}`" :src="require(`~/assets/Weapons/${image}`)" style="height: 416px; width: 288px; object-fit: none;"/>
    <br>
    <p>{{alt_text}}</p>
    <br>
    <aspect></aspect>
    <b-button size="sm" v-on:click="randomize(); ">randomize</b-button>
  </div>
</template>

<script>
import hades from '~/assets/data.json';
import {getRandomInt} from "~/assets/helper.js";
import Aspect from "~/components/Aspect";

export default {
  name: "Weapon",
  components: {Aspect},
  props: ['weapon'],
  data () {
    let i = getRandomInt(0,hades.Weapons.length - 1);
    let weapon = hades.Weapons[i];

    return {
      componentKey: 0,
      image: weapon.img,
      alt_text : weapon.name + ", "  + weapon.alt_name
    }
  },
  methods : {
    randomize : function (event) {
      let i = getRandomInt(0, hades.Weapons.length - 1)
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

</style>
