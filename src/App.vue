<template>
  <div id="app">
    <h1 style="textAlign: center;">Only dynamic two way binding and BootstrapVue</h1>
    <hr>
    <b-alert show variant="primary" style="textAlign: center;">The infamous Monster-Slayer...</b-alert>

    <hr>
    <b-row>
      <b-col>
        <app-simple-monster :monsterHealth="monsterHealth" :info="info" :infoEnemy="infoEnemy">
        </app-simple-monster>
      </b-col>
      <b-col>
        <app-player :playerHealth="playerHealth"  :info="info" :infoPlayer="infoPlayer">
        </app-player>
      </b-col>
    </b-row>

     <b-row>
      <b-col style="textAlign: center;">
        <app-menu :playerAttack="playerAttack" :playerSpecial="playerSpecial" :playerHeal="playerHeal" :runAway="runAway">
        </app-menu>
      </b-col>
    </b-row>


    <b-row>
      <b-col>
        <app-turns>
          <p slot="dmgP" v-for="dmgP in playerDmg" :key="dmgP">{{dmgP.item}}</p>
          <p slot=dmgM v-for="dmgM in monsterDmg" :key="dmgM">{{dmgM.item}}</p>
        </app-turns>
      </b-col>
    </b-row>

  </div>
</template>

<script>
import Player from "./Comps/Player.vue";
import Menu from "./Comps/Menu.vue";
import SimpleMonster from "./Comps/SimpleMonster.vue";
import Turns from "./Comps/Turns.vue";

export default {
  data() {
    return {
      gameOn: false,
      monsterHealth: 100,
      playerHealth: 100,
      info: {
        player: "Fight ...",
        enemy: " Fight ..."
      },
      infoPlayer: "Fight ?",
      infoEnemy: "Fight ?",
      damage: Number,
      playerDmg: [],
      monsterDmg: []
    };
  },
  components: {
    appSimpleMonster: SimpleMonster,
    appPlayer: Player,
    appMenu: Menu,
    appTurns: Turns
  },
  methods: {
    setGame() {
      this.info.player = "Fight !";
      this.info.enemy = "Fight !";
      this.infoPlayer = "Fight !";
      this.infoEnemy = "Fight !";
      this.playerDmg = [];
      this.monsterDmg = [];
      this.playerHealth = 100;
      this.monsterHealth = 100;
    },
    playerAttack() {
      this.damage = this.calculateDamage(3, 10);
      this.monsterHealth = this.monsterHealth - this.damage;
      this.info.player = "Hit " + this.damage;
      this.monsterAttacks();
      this.damage = 0;
      this.playerDmg.unshift({
        item: this.info.player
      });
    },
    playerSpecial() {
      this.damage = this.calculateDamage(10, 20);
      this.monsterHealth = this.monsterHealth - this.damage;
      this.info.player = "Special: " + this.damage;
      this.monsterAttacks();
      this.damage = 0;
      this.playerDmg.unshift({
        item: this.info.player
      });
    },
    playerHeal() {
      let heal = this.calculateDamage(8, 16);
      let info = "";
      if (this.playerHealth <= 90) {
        this.playerHealth += heal;
        this.info.player = "Heals " + heal;
      } else {
        this.playerHealth = 100;
        this.info.player = "Almost ...";
      }
      this.playerDmg.unshift({ item: this.info.player });
      /*
      this.monsterDmg.unshift({ item: this.info.player });
      */
      this.monsterAttacks();
    },
    runAway() {
      alert("You really will run away you Coward ?");
      this.setGame();
    },
    calculateDamage(min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    checkWin() {
      if (this.monsterHealth <= 0) {
        this.setGame();
        alert("New Round");
      } else if (this.playerHealth <= 0) {
        this.setGame();
        alert("New Round you lost ...");
      }
    },
    monsterAttacks() {
      let mDamage = this.calculateDamage(5, 12);
      this.playerHealth = this.playerHealth - mDamage;
      this.info.enemy = "Monster : " + mDamage;
      this.monsterDmg.unshift({
        item: this.info.enemy
      });
      this.checkWin();
    }
  },
  computed: {}
};
</script>

<style scoped>
.fixer {
  position: absolute;
  text-align: center;
}
</style>
