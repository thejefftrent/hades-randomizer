 <template>
  <div class="container">
    <div>
      <h1 class="title">
        Hades Randomizer
      </h1>
      <Weapon v-bind:aspectIndex="weaponRolls.aspectIndex" v-bind:weaponIndex="weaponRolls.weaponIndex" />
      <Mirror v-bind:mirror-items="mirrorRolls" />

    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import Weapon from "~/components/Weapon.vue";
import Aspect from "~/components/Aspect.vue";
import MirrorItem from "~/components/MirrorItem.vue";
import hades from "~/assets/data.json";
import {getRandomInt} from "~/assets/helper";
import Mirror from "~/components/Mirror.vue";

export default Vue.extend({
  components: {Mirror, MirrorItem, Aspect, Weapon},
  data () {
    //determine mirrorRolls
    let mirrorRolls = hades.Mirror.map(x => {
      let flip = getRandomInt(0, 2);
      return {
        color: flip ? 'm-green' : 'm-orange',
        name: x[flip]
      };
    });

    // Get Weapon Rolls
    let weaponRolls = {
      weaponIndex : getRandomInt(0, hades.Weapons.length),
      aspectIndex : getRandomInt(0, 4), //there are always 4 aspects
    }
    return {
      mirrorRolls : mirrorRolls,
      weaponRolls : weaponRolls
    }
  },
  methods : {
    getMirrorRolls : function () {

    },
  }
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
