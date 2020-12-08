 <template>
  <div class="container">
    <div>
      <h1 class="title">
        Hades Randomizer
      </h1>
      <Weapon />
      <Aspect />
<!--      <Mirror v-bind:mirror-items="mirrorRolls" />-->
<!--      <MirrorItem v-bind:color="m.color" v-for="m in mirrorRolls"> </MirrorItem>-->
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import Weapon from "~/components/Weapon.vue";
import Aspect from "~/components/Aspect.vue";
import MirrorItem from "~/components/MirrorItem.vue";
import hades from "~/assets/data.json";
import {getRandomInt} from "~/assets/helper";
import Mirror from "~/components/Mirror.vue";

export default Vue.extend({
  components: {Mirror, MirrorItem, Aspect, Weapon},
  data () {
    let mirrorRolls = hades.Mirror.map(x => {
      let flip = getRandomInt(0, 2);
      return {
        color: flip ? 'm-green' : 'm-orange',
        name: x[flip]
      };
    });
    return {
      mirrorRolls : mirrorRolls
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
