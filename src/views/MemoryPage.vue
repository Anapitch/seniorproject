<template>
  <ion-page>
    <ion-content>
      <div>
        <ion-icon
          :src="chevronBack"
          class="icon"
          @click="$router.push('/game')"
        ></ion-icon>
      </div>
      <h1>Memory Game</h1>
      

      <div class="time_score">
        <div class="time">Time <span id="time">90</span></div>
        <ion-button class="btn_reset">reset</ion-button>
        <div class="score">Score: <span id="score">0</span></div>
      </div>

      <div class="cards">
        <div class="card" v-for="(info, index) in info" :key="index">
          <img :src="info.image" />
        </div>
        <div class="card" v-for="(info2, index) in info2" :key="index">
          <img :src="info2.image" />
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonContent, IonButton } from "@ionic/vue";
import { defineComponent } from "vue";
import { chevronBack} from "ionicons/icons";
import axios from "axios";


export default defineComponent({
  name: "QuizPage",
  components: {
    IonPage,
    IonContent,
    IonButton, 
  },
  setup() {
    return {
      chevronBack,
    };
  },
  data() {
    return {
      info: [],
      info2: [],
    };
  },
  
  mounted() {
    axios.get("http://localhost:8000/memory").then((response) => {
      this.info = response.data;
      console.log(response);
    });
    axios.get("http://localhost:8000/textmemory").then((response) => {
      this.info2 = response.data;
      console.log(response);
    });
  },
});
</script>

<style scoped>
ion-content {
  --ion-background-color: rgba(1, 36, 53, 1);
}

h1 {
  color: aliceblue;
  font-size: 1.3rem;
  text-align: center;
  margin-top: -37px;
}

.icon {
  color: aliceblue;
  font-size: 2em;
  margin-top: 20px;
}

.btn_reset {
  width: 50px;
  height: 30px;
  margin-left: 133px;
  margin-top: -27px;
}

.cards {
  display: grid;
  grid-template-columns: 85px 85px 85px;
  grid-template-rows: 68px 68px 68px 68px 68px 68px;
  grid-gap: 5px;
  justify-content: center;
  margin-top: 20px;
}

.card {
  background-color: #ff8a00;
}
.card:hover img {
  transform: scale(1.03);
  opacity: 1;
}

.card:hover  {
  background-color: rgb(255, 254, 254);
}
.card img {
  width: 75%;
  height: 75%;
  margin-left: 11px;
  margin-top: 7px;
  opacity: 0;
  transition: 0.3s all ease;
}

p {
  font-size: 15px;
  font-weight: 500;
  text-align: center;
  margin-top: 25px;
  opacity: 0;
}

p:hover {
  opacity: 1;
}

p:hover {
  background-color: rgb(255, 254, 254);
  
}

.time_score {
  display: grid;
}

.time {
  color: aliceblue;
  font-size: 1rem;
  margin-left: 20px;
  margin-top: 20px;
}

.score {
  color: aliceblue;
  font-size: 1rem;
  margin-left: 235px;
  margin-top: -30px;
}
</style>

