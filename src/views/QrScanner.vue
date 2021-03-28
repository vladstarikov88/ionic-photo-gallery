<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Photo Gallery</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <template v-if="error">
        <p class="error--text">{{ error }}</p>
      </template>

      <div class="qr-code-scanner">
        <qrcode-stream 
          @decode="onDecode"
          @init="onInit"
        />
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import { IonContent, IonPage, IonHeader, IonToolbar, IonTitle } from '@ionic/vue';
import { QrcodeStream } from 'vue-qrcode-reader';
import { ref } from 'vue';

export default {
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    QrcodeStream
  },
  setup() {
    const error = ref('');
    const result = ref('');

    const onDecode = (res) => {
      result.value = res;
      window.open(res, '_blank').focus();
    }

    const onInit = async (promise) => {
      try {
        await promise;
      } catch (e) {
        error.value = e;
      }
    }

    return {
      onDecode,
      onInit
    }
  }
};
</script>

<style scoped>
.frame {
  width: 90%;
  height: 80vh;
}

.qr-code-scanner {
  margin: 0 auto;
  width: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
