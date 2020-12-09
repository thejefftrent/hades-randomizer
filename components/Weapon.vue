<template>
  <div>
    <h3>{{ weaponName }}</h3>
    <img class="weapon-img" :alt="`${weaponName}`" :src="require(`~/assets/Weapons/${weaponImg}`)"/>
    <aspect v-bind:weaponIndex="weaponIndex" v-bind:aspectIndex="aspectIndex"></aspect>
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
  data() {
    return {
      weaponIndex: this.weaponIndex,
      aspectIndex: this.aspectIndex,
      weaponImg: hades.Weapons[this.weaponIndex].img,
      weaponName: `${hades.Weapons[this.weaponIndex].alt_name}, ${hades.Weapons[this.weaponIndex].name}`
    }
  },
  methods: {
    randomize: function (event) {
      let i = getRandomInt(0, hades.Weapons.length)
      let weapon = hades.Weapons[i];
      this.image = weapon.img;
      this.alt_text = weapon.name + ", " + weapon.alt_name;
      //alert(`${hades.Weapons[this.i].name}`);
    },
    setWeapon: function (index) {
      let weapon = hades.Weapons[index];
      this.image = weapon.img;
      this.alt_text = weapon.name + ", " + weapon.alt_name;
    },
  },
  watch: {
    weaponIndex:  {
      immediate: true,
      handler (newVal, oldVal) {
        this.weaponImg = hades.Weapons[newVal].img;
        this.weaponName = `${hades.Weapons[newVal].alt_name}, ${hades.Weapons[newVal].name}`;
      }
    }
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
