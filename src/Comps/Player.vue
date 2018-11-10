<template>
  <div style="textAlign: center;">
    <h5>{{info.player}}</h5>
     <hr>
    <h4>Player</h4>

    <b-row>
      <b-col>
        <b-alert show :style="{width: playerHealth + '%'}"> {{playerHealth}}</b-alert>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  props: {
    playerHealth: Number,
    info: Object
  },
  data() {
    return {};
  },
  methods: {},
  created() {}
};
</script>

<style>
</style>
