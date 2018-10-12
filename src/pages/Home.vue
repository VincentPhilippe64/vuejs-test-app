<template>
<div id="BJgqjQDs5Q">
  <mdc-top-app-bar class="ByGVRrws5Q" title="Zentral+">
    <mdc-top-app-bar-action class="Helpbutton_upright" icon="more_vert" v-on:click='MoreHelp'></mdc-top-app-bar-action>
  </mdc-top-app-bar>
  <mdc-list class="ry7EKIDo9Q" bordered two-line interactive>
    <mdc-list-item v-for="item in items" v-on:click="GoToPageLink(item)">
      {{ item.title }}
      <div class="item-type">
        {{ item.type }}
      </div>
      <div class="secondInfo">
        👁 {{ item.reads }}
      </div>
      <div class="thirdInfo">
        🗨 {{ item.comments_count }}
      </div>
    </mdc-list-item>
  </mdc-list>
  <mdc-fab class="FAB_refresh" icon="refresh" v-on:click="LoadData"></mdc-fab>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'home', // notre module
  methods: { // tous les fonctions ..


    GoToPageLink: function(i) {
      window.open(i.url);
      console.log(i.url);
    },


    LoadData: function() {

      var self = this;
      var url = '/static/test-data.json';

      // Ajax request
      // get JSON (url)
      // self.data.items = ...

        axios.get(url).then(function(response) {
          console.log(response.data);
          self.items = response.data.items;


        })

    }


  },
  data () {
    return { // tous les données ..


      items: []


    }
  },
  mounted () {
    this.LoadData();
}


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#BJgqjQDs5Q {
  --mdc-theme-primary: rgb(144, 0, 0);
  --mdc-theme-secondary: rgb(144, 0, 0);
  --mdc-theme-background: #ffffff;
  position: relative;
  margin: auto;
  background-color: #ffffff;
  overflow: hidden;
  width: 100%;
  height: 100%;
}

.ry7EKIDo9Q {
  overflow: hidden;
  position: absolute;
  width: calc(100% - 0px - 0px);
  height: 100%;
  top: 64px;
  left: 0px;
  bottom: -64px;
  right: auto;
}

.FAB_refresh {
  margin-right: 16dp;
  margin-bottom: 16dp;
}

.item-type {
  background-color: #900000;
  padding: 3px 5px;
  color: #FFFFFF;
  font-size: 100%;
  margin-left: 1em;
  border-radius: 2px;
}

.secondInfo {
  background-color: #333333;
  padding: 3px 5px;
  color: #FFFFFF;
  font-size: 100%;
  margin-left: 0.5em;
  border-radius: 2px;
}

.thirdInfo {
  background-color: #DDDDDD;
  padding: 3px 5px;
  color: #333333;
  font-size: 100%;
  margin-left: 0.5em;
  border-radius: 2px;
}

</style>
