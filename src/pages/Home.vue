<template>
<div id="BJgqjQDs5Q">
  <mdc-top-app-bar class="ByGVRrws5Q" title="Zentral+">
    <mdc-top-app-bar-action class="Helpbutton_upright" icon="more_vert"></mdc-top-app-bar-action>
  </mdc-top-app-bar>
  <mdc-list class="ry7EKIDo9Q" bordered two-line interactive>
    <mdc-list-item v-for="item in items" v-on:click="GoToPageLink(item)">
        {{ item.headline }}
        {{ item.subheading }}
    </mdc-list-item>
  </mdc-list>
  <mdc-fab class="FAB_refresh" icon="refresh"></mdc-fab>
</div>
</template>

<script>
export default {
  name: 'home', // notre module
  methods: { // tous les fonctions ..


    GoToPageLink: function(i) {
      window.open(i.link);
    },


    LoadData: function() {

      var self = this;
      var url = '/static/test-data.json';

      // Ajax request
      // get JSON (url)
      // self.data.items = ...

        var titleOfNewsHeadline = axios.get('/static/test-data.json/items/0/title');
            

    }


  },
  data () {
    return { // tous les données ..


      items: [
        {
          headline: titleOfNewsHeadline,
          subheading: 'Diese Musik darf man in Luzern nicht verpassen',
          link: 'https://www.zentralplus.ch/de/news/kultur/5579039/10-Konzert-Highlights-f%C3%BCr-die-kalten-Tage.htm'
        },
        { message: 'Mozilla Firefox' },
        { message: 'Micorosft Edge' }
      ]


    }
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

</style>
