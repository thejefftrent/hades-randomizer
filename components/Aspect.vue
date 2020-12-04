<template>
  <div>
    <img :alt="`${alt_text}`" :src="require(`~/assets/Weapons/Aspects/${image}`)" style="height: 100px; width: 100px; object-fit: scale-down;"/>
    <p>{{alt_text}}</p>
  </div>

</template>

<script>
import hades from '~/assets/data.json';
import {getRandomInt} from "~/assets/helper.js";
export default {
  name: "Aspect",
  data () {
    let i = getRandomInt(0, hades.Weapons.length)
    let aspect = hades.Weapons[i].aspects[getRandomInt(0,hades.Weapons[i].aspects.length)];
    return {
      weaponIndex: i,
      image : aspect.img,
      alt_text : aspect.name
    }
  },
  methods : {
    setAspect : function (index) {
      let i = index % hades.Weapons[this.weaponIndex].aspects.length;
      let aspect = hades.Weapons[this.weaponIndex].aspects[i];
      this.image = aspect.img;
      this.alt_text = aspect.name;
    }
  }
}
</script>

<style scoped>

</style>
