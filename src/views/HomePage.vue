<template>

  <ion-page>

    <ion-header>

      <ion-toolbar color="light">

        <ion-title>
          Data Cryptocurrency
        </ion-title>

      </ion-toolbar>

    </ion-header>

    <ion-content>

      <div class="btn-area">

        <ion-button @click="loadData">
          Refresh
        </ion-button>

      </div>

      <CryptoListItem
        v-for="(coin, index) in cryptos"
        :key="index"
        :crypto="coin"
      />

    </ion-content>

  </ion-page>

</template>

<script lang="ts">

import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonButton
} from '@ionic/vue';

import { defineComponent } from 'vue';
import axios from 'axios';

import CryptoListItem from '@/components/CryptoListItem.vue';

export default defineComponent({

  name: 'HomePage',

  components: {
    IonPage,
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonButton,
    CryptoListItem
  },

  data() {

    return {

      cryptos: [] as any[]

    };

  },

  mounted() {

    this.loadData();

  },

  methods: {

    loadData() {

      axios
        .get('https://api.coinlore.net/api/tickers/')

        .then((response) => {

          this.cryptos = response.data.data.slice(0, 20);

        })

        .catch((error) => {

          console.error('Gagal mengambil data:', error);

        });

    }

  }

});

</script>

<style scoped>

.btn-area {
  text-align: center;
  padding: 15px;
}

</style>