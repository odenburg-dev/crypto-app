<template>

  <ion-card class="crypto-card">

    <ion-grid>

      <ion-row>

        <ion-col size="3">

          <div class="label">
            Rank
          </div>

          <div class="rank">
            {{ crypto.rank }}
          </div>

        </ion-col>

        <ion-col size="5">

          <div class="label">
            {{ crypto.name }}
          </div>

          <div class="symbol">
            {{ crypto.symbol }}
          </div>

        </ion-col>

        <ion-col size="4">

          <div class="label">
            USD
          </div>

          <div class="price">
            {{ crypto.price_usd }}
          </div>

        </ion-col>

      </ion-row>

    </ion-grid>

  </ion-card>

</template>

<script lang="ts">
import {
  IonCard,
  IonGrid,
  IonRow,
  IonCol
} from '@ionic/vue';

import { defineComponent, PropType } from 'vue';

interface Crypto {
  rank: string;
  name: string;
  symbol: string;
  price_usd: string;
}

export default defineComponent({

  name: 'CryptoListItem',

  props: {
    crypto: {
      type: Object as PropType<Crypto>,
      required: true
    }
  },

  components: {
    IonCard,
    IonGrid,
    IonRow,
    IonCol
  }

});
</script>

<style scoped>

.crypto-card{
  margin:0;
  border-radius:0;
  background:#F3E9C7;
  box-shadow:none;
  border-bottom:1px solid #D6B95F;
}

.label{
  font-size:16px;
  color:#1b1a1a;
}

.rank{
  font-size:30px;
  font-weight:bold;
  color:#1b1a1a;
}

.symbol{
  font-size:30px;
  font-weight:bold;
  color:#1b1a1a;
}

.price{
  font-size:29px;
  font-weight:bold;
  color:#1b1a1a;
}

</style>