<template>
  <div>
    <div class="top-row">
      <!-- <div class="robot-name">
        {{selectedRobot.head.title}}
        <span class="sale" v-show="selectedRobot.head.onSale">SALE!</span>
      </div> -->
      <part-selector position="top" :parts="availableParts.heads"/>
    </div>
    <div class="middle-row">
      <part-selector position="left" :parts="availableParts.arms"/>
      <part-selector position="center" :parts="availableParts.torsos"/>
      <part-selector position="right" :parts="availableParts.arms"/>
    </div>
    <div class="bottom-row">
      <part-selector position="bottom" :parts="availableParts.bases"/>
    </div>
    <div class="cart">
      <button @click="addToCard()">Add to Cart</button>
      <table>
        <thead>
          <tr>
            <th>Robot</th>
            <th>Cost</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(robot, index) in cart" :key="index">
            <td>{{robot.head.title}}</td>
            <td>{{robot.cost}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import PartSelector from '../components/PartSelector.vue';
import availableParts from '../data/parts';
import lifecycleMixins from '../mixins/lifecycle-mixins';

export default {
  components: { PartSelector },
  name: 'RobotBuilder',
  props: {
    msg: String,
  },
  data() {
    return {
      availableParts, // property shorthand for "availableParts: availableParts"
      selectedRobot: {
        head: {},
        leftArm: {},
        torso: {},
        rightArm: {},
        base: {},
      },
      cart: [],
    };
  },
  mixins: [lifecycleMixins],
  methods: {
    addToCard() {
      const robot = this.selectedRobot;
      const cost = robot.head.cost
        + robot.leftArm.cost + robot.torso.cost + robot.rightArm.cost
        + robot.base.cost;
      // this.cart.push(Object.assign({}, robot, { cost }));
      const cartRobot = { ...robot, ...{ cost } };
      console.log(cartRobot);
      // {head: {…}, leftArm: {…}, torso: {…}, rightArm: {…}, base: {…}, cost: xxx}
      this.cart.push(cartRobot);
    },
  },
  created() {
    console.log('zhangle:created()');
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.top-row {
  display:flex;
  justify-content: space-around;
}
.middle-row {
  display:flex;
  justify-content: center;
}
.bottom-row {
  display:flex;
  justify-content: space-around;
  border-top: none;
}
.sale {
  color: red;
}
</style>
