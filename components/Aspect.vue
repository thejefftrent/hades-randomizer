<template>
  <div class="aspect-block">
    <img class="aspect-img" :alt="`${aspectName}`" :src="require(`~/assets/Weapons/Aspects/${aspectImg}`)"/>
    <p>{{aspectName}}</p>
  </div>

</template>

<script>
import hades from '~/assets/data.json';
import {getRandomInt} from "~/assets/helper.js";
export default {
  name: "Aspect",
  props: {
    weaponIndex: Number,
    aspectIndex: Number
  },
  data () {
    return {
      aspectName: hades.Weapons[this.weaponIndex].aspects[this.aspectIndex].name,
      aspectImg: hades.Weapons[this.weaponIndex].aspects[this.aspectIndex].img
    }
  },
  methods : {
    setAspect : function (index) {
      let i = index % hades.Weapons[this.weaponIndex].aspects.length;
      let aspect = hades.Weapons[this.weaponIndex].aspects[i];
      this.image = aspect.img;
      this.alt_text = aspect.name;
    }
  },
  watch: {
    weaponIndex:  {
      immediate: true,
      handler (newVal, oldVal) {
        this.aspectName = hades.Weapons[newVal].aspects[this.aspectIndex].name;
          this.aspectImg = hades.Weapons[newVal].aspects[this.aspectIndex].img;
      }
    },
    aspectIndex:  {
      immediate: true,
      handler (newVal, oldVal) {
        this.aspectName = hades.Weapons[this.weaponIndex].aspects[newVal].name;
        this.aspectImg = hades.Weapons[this.weaponIndex].aspects[newVal].img;
      }
    },

  }
}
</script>

<style scoped>
.aspect-img {
  height: 100px;
  width: 100px;
  object-fit: scale-down;
}
.aspect-block {
  display: inline-block;
  float: bottom;
}
</style>
