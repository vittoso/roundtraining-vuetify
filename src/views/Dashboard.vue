<template>
  <div>
    <h1>Dashboard</h1>
    <v-data-table
      :headers="headers"
      :items="employees"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
      multi-sort="true"
    ></v-data-table>

    <v-snackbar v-model="snackbar">
      You have selected {{ selectedEmployee.title }} {{ selectedEmployee.name }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </div>
</template>

<script>
import employeesData from "../data/employees.json";

export default {
  data() {
    return {
      selectedEmployee: "",
      snackbar: false,
      headers: [
        { text: "ID", align: "left", value: "id" },
        { text: "Name", align: "left", value: "name" },
        { text: "Title", value: "title" },
        { text: "Salary", value: "salary", align: "right" }
      ],
      employees: employeesData
    };
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.selectedEmployee = event;
    }
  }
};
</script>

<style scoped></style>
