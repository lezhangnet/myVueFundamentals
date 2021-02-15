<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <div class="robot-name">
          {{selectedRobot.head.title}}
          <span class="sale" v-show="selectedRobot.head.onSale">SALE!</span>
        </div>
        <img v-bind:src="selectedRobot.head.src" title="head"/>
        <button v-on:click="selectHead" class="prev-selector">&#9668;</button>
        <button v-on:click="selectHead" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="selectedRobot.leftArm.src" title="left arm"/>
        <button v-on:click="selectLeftArm" class="prev-selector">&#9650;</button>
        <button v-on:click="selectLeftArm" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="selectedRobot.torso.src" title="torso"/>
        <button v-on:click="selectTorso" class="prev-selector">&#9668;</button>
        <button v-on:click="selectTorso" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="selectedRobot.rightArm.src" title="right arm"/>
        <button v-on:click="selectRightArm" class="prev-selector">&#9650;</button>
        <button v-on:click="selectRightArm" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="selectedRobot.base.src" title="base"/>
        <button v-on:click="selectBase" class="prev-selector">&#9668;</button>
        <button v-on:click="selectBase" class="next-selector">&#9658;</button>
      </div>
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
import availableParts from '../data/parts';

export default {
  name: 'RobotBuilder',
  props: {
    msg: String,
  },
  data() {
    return {
      availableParts,
      headIndex: 0,
      leftArmIndex: 0,
      torsoIndex: 0,
      rightArmIndex: 0,
      baseIndex: 0,
      cart: [],
    };
  },
  computed: {
    selectedRobot() {
      return {
        head: availableParts.heads[this.headIndex],
        leftArm: availableParts.arms[this.leftArmIndex],
        torso: availableParts.torsos[this.torsoIndex],
        rightArm: availableParts.arms[this.rightArmIndex],
        base: availableParts.bases[this.baseIndex],
      };
    },
  },
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
    selectHead() {
      this.headIndex += 1;
    },
    selectLeftArm() {
      this.leftArmIndex += 1;
    },
    selectTorso() {
      this.torsoIndex += 1;
    },
    selectRightArm() {
      this.rightArmIndex += 1;
    },
    selectBase() {
      this.baseIndex += 1;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.part {
  position: relative;
  width:165px;
  height:165px;
  border: 3px solid #aaa;
}
.part img {
  width:165px;
}
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
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index:1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector, .center .next-selector {
  opacity:0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
.sale {
  color: red;
}
</style>
