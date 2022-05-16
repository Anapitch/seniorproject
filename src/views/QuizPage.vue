<template>
  <ion-page>
    <ion-content>
      <meta charset="utf-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1" />
      <link
        rel="stylesheet"
        href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css"
      />
      <div class="top-section">
        <ion-icon
          :src="chevronBack"
          class="icon"
          @click="$router.push('/game')"
        ></ion-icon>
        <h1 class="text">Quiz Game</h1>
      </div>

      <ion-grid fixed>
        <ion-row>
          <ion-col size="12" router-link="/text">
           
            </ion-col>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonContent, IonGrid, IonRow, IonCol } from "@ionic/vue";
import { defineComponent } from "vue";
import { chevronBack, volumeMediumOutline } from "ionicons/icons";

export default defineComponent({
  name: "QuizPage",
  components: {
    IonPage,
    IonContent,
    IonGrid,
    IonRow,
    IonCol,
  },
  setup() {
    return {
      chevronBack,
      volumeMediumOutline,
    };
  },
});
</script>

<style scoped>
ion-content {
  --ion-background-color: rgba(1, 36, 53, 1);
}

.top-section {
  min-height: 200px;
  border-bottom-left-radius: 40px;
  border-bottom-right-radius: 40px;
  background-color: #ff8a00;
  padding-top: 100px;
}

.icon {
  width: 2.5rem;
  height: 2.5rem;
  transform: translateY(-12vh);
  margin-left: 5px;
  font-weight: 600;
}

.text {
  font-size: 2.3rem;
  text-align: center;
  font-family: serif;
  transform: translateY(-20.5vh);
  font-weight: 100;
}

ion-grid {
  margin-top: -145px;
}

ion-col {
  max-width: auto;
  height: 460px;
  background-color: rgba(48, 50, 58, 1);
  border-radius: 20px;
  display: block;
  margin: 18px 0;
}
</style>

