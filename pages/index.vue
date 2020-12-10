 <template>
  <div class="container">
    <div>
      <h1 class="title">
        Hades Randomizer
      </h1>
      <b-button size="sm" v-on:click="randomize(); ">randomize</b-button>
      <Weapon v-bind:aspectIndex="aspectIndex" v-bind:weaponIndex="weaponIndex" />
      <Items v-bind:item-rolls="itemRolls"/>
      <Mirror v-bind:mirror-items="mirrorRolls" />
      <Heat v-bind:heat-items="heatRolls" v-on:change-budget="updateHeat($event)"/>
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
import Heat from "@/components/Heat";
import Items from "@/components/Items";

export default Vue.extend({
  components: {Items, Heat, Mirror, MirrorItem, Aspect, Weapon},
  data () {
    return {
      mirrorRolls : this.getMirrorRolls(),
      weaponIndex : this.getWeaponRolls().weaponIndex,
      aspectIndex : this.getWeaponRolls().aspectIndex,
      heatBudget : 20,
      heatRolls : this.getHeatRolls(this.heatBudget),
      itemRolls : this.getItemRolls()
    }
  },
  methods : {
    getWeaponRolls : function () {
      return {
        weaponIndex : getRandomInt(0, hades.Weapons.length),
        aspectIndex : getRandomInt(0, 4), //there are always 4 aspects
      }
    },
    getMirrorRolls : function () {
      return hades.Mirror.map(x => {
        let flip = getRandomInt(0, 2);
        return {
          color: flip ? 'm-green' : 'm-orange',
          name: x[flip]
        };
      });
    },
    getHeatRolls : function (heatAmount) {
      let heat = hades["Pact of Punishment"].map(x => {
        x.amount = 0
        return x
      });
      let counter = 0;
      while (heatAmount > 0) {
        counter++;
        let randomHeat = heat[getRandomInt(0,heat.length)];
        //check if there are remaining slots and if we can afford the next level
        if(randomHeat.amount < randomHeat.cost.length && randomHeat.cost[randomHeat.amount] <= heatAmount) {
          console.log(`Heat Budget is ${heatAmount}. Buying ${randomHeat.name} for ${randomHeat.cost[randomHeat.amount]}.`);
          heatAmount -= randomHeat.cost[randomHeat.amount];
          randomHeat.amount++;
          counter = 0;
        }
        if (counter === 20) {
          break;
        }
      }
      return heat;
    },
    randomize : function() {
      this.mirrorRolls = this.getMirrorRolls();
      let weaponRolls = this.getWeaponRolls();
      this.weaponIndex = weaponRolls.weaponIndex;
      this.aspectIndex = weaponRolls.aspectIndex;
      this.heatRolls = this.getHeatRolls(this.heatBudget);
      this.itemRolls = this.getItemRolls();
    },
    updateHeat : function(heatBudget) {
      this.heatBudget = heatBudget;
      this.heatRolls = this.getHeatRolls(heatBudget);
    },
    getItemRolls : function () {
      let rolls = {
        companion : {
          companionName : "",
          companionImg : ""
        },
        keepsakes : []
      };
      let companion = hades.Companions[getRandomInt(0,hades.Companions.length)];
      rolls.companion.companionName = companion.name;
      rolls.companion.companionImg = companion.img;
      // let keepsakes = JSON.parse(JSON.stringify(hades.Keepsakes));
      let keepsakes = [...hades.Keepsakes]
      for (let i = 0; i < 4; i++) {
        let randomKeepsake = keepsakes.splice(getRandomInt(0,keepsakes.length),1)[0];
        rolls.keepsakes.push(randomKeepsake);
      }
      return rolls;
    }
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
