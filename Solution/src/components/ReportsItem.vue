
   
<template>
  <ion-grid class="reports-item-grid-padding">
    <ion-row class="reports-item-data-row">
      <ion-col class="ion-padding-vertical" size="4">
        <div class="reports-item-top-row-id">ID: {{ reportId }}</div>
        <div class="reports-item-bottom-row">State: {{ report.state }}</div>
      </ion-col>
      <ion-col class="ion-padding-vertical" size="4">
        <div class="reports-item-top-row">
          Type:
          {{ report.payload.reportType }}
        </div>
        <div class="reports-item-bottom-row">Message: {{ message }}</div>
      </ion-col>
      <ion-col size="4">
        <div>
          <ion-button @click="dataDestroyObject(report.id)" expand="block">
            Destroy
          </ion-button>
        </div>
        <div>
          <ion-button @click="dataTakeInObject(report.id)" expand="block">
            Take In
          </ion-button>
        </div></ion-col
      >
    </ion-row>
  </ion-grid>
</template>

<script>
import { mapActions } from "vuex";
import { IonButton, IonCol, IonGrid, IonRow } from "@ionic/vue";
export default {
  name: "ReportsItem",
  components: {
    IonButton,
    IonCol,
    IonGrid,
    IonRow,
  },
  props: {
    report: Object,
  },
  computed: {
    reportId() {
      const reportId = this.report.id.slice(-12); // Extracts the last 12 characters of id.
      return reportId;
    },
    message() {
      const message = this.report.payload.message.toUpperCase(); // Converts message to Upper Case
      return message;
    },
  },
  methods: {
    ...mapActions("data", ["dataDestroyObject", "dataTakeInObject"]),
  },
};
</script>

<style scoped>
.reports-item-grid-padding {
  padding: 0px;
}
.reports-item-data-row {
  border-bottom: 1px solid #3880ff;
  border-top: 1px solid #3880ff;
  border-right: 2px solid #3880ff;
  border-left: 2px solid #3880ff;
}
.reports-item-top-row {
  font-size: 15px;
  line-height: normal;
}
.reports-item-bottom-row {
  line-height: normal;
  padding-top: 15px;
}
.reports-item-top-row-id {
  font-size: 15px;
  line-height: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 1; /* number of lines to show */
  -webkit-box-orient: vertical;
}
</style>