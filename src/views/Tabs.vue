<template>
  <ion-page>
    <ion-content>
      <ion-tabs>
        <ion-tab-bar slot="bottom">
          <ion-tab-button tab="tab2" href="/tabs/tab2">
            <ion-icon :icon="images" />
            <ion-label>Photos</ion-label>
          </ion-tab-button>
          
          <ion-tab-button tab="qr-scanner" href="/tabs/qr-scanner">
            <ion-icon :icon="qrCodeOutline" />
            <ion-label>QR scanner</ion-label>
          </ion-tab-button>
        </ion-tab-bar>
      </ion-tabs>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonContent, IonLabel, IonIcon, IonPage } from '@ionic/vue';
import { images, square, triangle, qrCodeOutline } from 'ionicons/icons';

export default {
  name: 'Tabs',
  components: { IonContent, IonLabel, IonTabs, IonTabBar, IonTabButton, IonIcon, IonPage },
  setup() {
    return {
      images, 
      square, 
      triangle,
      qrCodeOutline,
    }
  }
}
</script>
