<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>{{ title }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <div class="reports-view-container">
        <h1>
          <ion-label class="reports-list-title">Reports</ion-label>
        </h1>

        <ion-card class="reports-card-container">
          <!-- Transition-group: Smooths the disappearing of a report item -->
          <transition-group name="fade" tag="list">
            <ReportsItem
              v-for="report in elements"
              :report="report"
              :key="report.id"
            />
          </transition-group>
        </ion-card>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import ReportsItem from "@/components/ReportsItem";
import { mapState } from "vuex";
import {
  IonContent,
  IonCard,
  IonHeader,
  IonLabel,
  IonPage,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Reports",
  components: {
    IonCard,
    IonHeader,
    IonContent,
    IonLabel,
    IonPage,
    IonTitle,
    IonToolbar,
    ReportsItem,
  },
  computed: {
    ...mapState("data", ["title", "elements"]),
  },
});
</script>

<style scoped>
.reports-list-title {
  display: flex;
  justify-content: left;
  font-size: 28px;
  padding: 0px 0px 0px 10px;
}
.reports-card-container {
  box-shadow: none;
}
@media screen and (min-width: 460px) {
  .reports-view-container {
    width: 450px;
    margin: auto;
  }
}
@media screen and (min-width: 520px) {
  .reports-view-container {
    width: 480px;
    margin: auto;
  }
}
@media screen and (min-width: 780px) {
  .reports-view-container {
    width: 680px;
    margin: auto;
  }
}

/* LIST TRANSITIONS */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scale(0.6);
}
.fade-leave-active {
  transition: all 0.7s ease;
  position: absolute;
}
.fade-enter-active {
  transition: all 0.7s ease;
}
.fade-move {
  transition: transform 0.7s ease;
}
</style>