<template>
  <div style="textAlign: center;">
    <h4>Easy Foe</h4>
    <b-alert show variant="danger" style="textAlign: center;"> {{monsterHealth}}</b-alert>
    <p>{{damageTaken}}</p>
    <slot name="damageDelivered"> </slot>
  </div>
</template>

<script>
import { fightRound } from "../main.js";

export default {
  props: {
    monsterHealth: Number,
    damageDelivered: Number,
    damageTaken: Number
  },
  data() {
    return {};
  },
  methods: {
    monsterAttacks() {
      fightRound.$emit("monsterAttack", (this.damage = 31));
    },
    created() {}
  }
};
</script>

<style>
</style>
