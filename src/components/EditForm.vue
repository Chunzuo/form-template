<template>
  <div>
    <div class="page" size="A4">
      <div class="container">
        <h3 class="text-center">Form Template</h3>

        <div style="display: flex; align-items: center">
          <span>This is a first text field</span>
          <v-text-field
            style="margin-left: 10px; width: 100px; margin-right: 10px;"
            v-model="data.text1"
          />
          <span>This is a second text field</span>
          <v-text-field
            style="margin-left: 10px;"
            width="50px"
            v-model="data.text2"
          />
        </div>

        <v-row class="ml-1" align="center">
          <span>Checkbox example:</span>
          <v-checkbox
            class="mr-2"
            label="Checkbox-1"
            value="Checkbox-1"
            v-model="data.checkbox"
          ></v-checkbox>
          <v-checkbox
            label="Checkbox-2"
            value="Checkbox-2"
            v-model="data.checkbox"
          ></v-checkbox>
        </v-row>

        <v-row class="ml-1" align="center">
          <span>Radio button example:</span>
          <v-radio-group row v-model="data.option">
            <v-radio label="Option 1" value="Option 1"></v-radio>
            <v-radio label="Option 2" value="Option 2"></v-radio>
          </v-radio-group>
        </v-row>
        <div>
          <div class="subheading">Image exmaple:</div>
          <v-img src="@/assets/img.jpg" aspect-ratio="2" />
        </div>
        <div class="mt-2">
          <span>Datepicker exmaple:</span>
          <v-menu
            ref="menu"
            v-model="menu"
            :close-on-content-click="false"
            :return-value.sync="date"
            transition="scale-transition"
            offset-y
            min-width="290px"
          >
            <template v-slot:activator="{ on }">
              <v-text-field
                v-model="date"
                label="Picker in menu"
                readonly
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker v-model="date" no-title scrollable>
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="menu = false">Cancel</v-btn>
              <v-btn text color="primary" @click="$refs.menu.save(date)"
                >OK</v-btn
              >
            </v-date-picker>
          </v-menu>
        </div>
      </div>
    </div>

    <div class="page" size="A4" id="print" v-show="false">
      <div class="container">
        <h3 class="text-center">Form Template</h3>

        <div style="display: flex; align-items: center">
          <span
            >This is a first text field
            <strong class="ml-1 mr-1">{{ data.text1 }}</strong> This is a second
            text field
            <strong class="ml-1 mr-1">{{ data.text2 }} </strong></span
          >
        </div>

        <v-row class="ml-1" align="center">
          <span>Checkbox example:</span>
          <strong
            v-for="(checkbox, index) in data.checkbox"
            :key="`checkbox-${index}1`"
          >
            {{ checkbox }}
          </strong>
        </v-row>

        <v-row class="ml-1" align="center">
          <span>Radio button example:</span>
          <strong>{{ data.option }}</strong>
        </v-row>
        <div>
          <div class="subheading">Image exmaple:</div>
          <img src="@/assets/img.jpg" alt="" />
        </div>
        <div class="mt-2">
          <span>Datepicker exmaple:</span>
          <strong>{{ date }}</strong>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      date: new Date().toISOString().substr(0, 10),
      menu: false,
      data: {
        checkbox: []
      }
    };
  }
};
</script>

<style lang="css" scoped>
.page {
  background: white;
  display: block;
  margin: 0 auto;
  margin-bottom: 0.5cm;
  box-shadow: 0 0 0.5cm rgba(0, 0, 0, 0.5);
}
.page[size="A4"] {
  width: 21cm;
  height: 29.7cm;
  margin-top: 0.5cm;
}
</style>
