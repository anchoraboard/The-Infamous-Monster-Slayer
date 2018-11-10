<template>
  <div>
    <b-row>
      <b-col class="simple-border">
        <b-button size="sm" variant="danger" @click="playerAttack()">Attack</b-button>
        <b-button size="sm" variant="warning" @click="playerSpecial()">Special</b-button>
        <b-button size="sm" variant="success" @click="playerHeal()">Heal</b-button>
        <b-button size="sm" variant="secondary" @click="runAway()">Run Away</b-button>
      </b-col>
    </b-row>

  </div>
</template>

<script>
export default {
  props: {
    playerAttack: Function,
    playerSpecial: Function,
    playerHeal: Function,
    runAway: Function
  },
  data() {
    return {};
  },
  methods: {},
  computed: {}
};
</script>

<style>
</style>
