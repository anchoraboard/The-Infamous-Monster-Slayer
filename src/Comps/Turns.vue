<template>
  <div style="textAlign: center;">
    <b-row>
      <b-col>
        <slot name="dmgP"></slot>
      </b-col>
      <b-col>
           <slot name="dmgM"></slot>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  props: ["info", "playerDmg", "monsterDmg"],
  data() {
    return {};
  },
  methods: {},
  created() {},
  computed: {}
};
</script>

<style>
</style>
