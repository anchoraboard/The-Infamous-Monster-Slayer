<template>
  <div style="textAlign: center;">
    <h5>{{info.enemy}}</h5>
    <h6>{{infoPlayer}}</h6>
    <hr>
    <h4>Easy Foe</h4>
    <b-row>
      <b-col>
        <b-alert show variant="danger" :style="{width: monsterHealth + '%'}"> {{monsterHealth}}</b-alert>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  props: {
    monsterHealth: Number,
    info: Object,
    infoPlayer: String
  },
  data() {
    return {};
  },
  methods: {}
};
</script>

<style>
</style>
