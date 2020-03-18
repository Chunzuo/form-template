<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <h2>Form Template</h2>
      </div>

      <v-spacer></v-spacer>

      <v-btn text @click="print">
        <span class="mr-2">Print</span>
        <v-icon>print</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <EditForm />
    </v-content>
  </v-app>
</template>

<script>
import EditForm from "./components/EditForm";

export default {
  name: "App",

  components: {
    EditForm
  },

  data: () => ({
    //
  }),
  methods: {
    print() {
      this.$htmlToPaper("print");
    }
  }
};
</script>
