<template>
  <main aria-labelledby="main-title" class="home">
    <header class="hero">
      <div>
        <img src="./b-editable-table-logo.png" alt="hero" />
        <h1 id="main-title">BootstrapVue Editable Table</h1>
        <p class="action">
          <a href="/guide/" class="nav-link action-button"> Get Started → </a>
        </p>
      </div>
      <div class="main-container">
        <b-card bg-variant="light">
          <h5 class="playground-title">Playground:</h5>
          <div v-if="inputValidation" class="required-description">
            <i>* Name is required</i> | <i>* Must select a department</i> |
            <i>* Must be 19 or older</i>
          </div>
          <div class="config-container">
            <b-form-group label="Edit Mode:">
              <b-form-radio
                v-model="editMode"
                value="cell"
                :disabled="customEdit"
                >Cell</b-form-radio
              >
              <b-form-radio
                v-model="editMode"
                value="row"
                :disabled="customEdit"
                >Row</b-form-radio
              >
            </b-form-group>
            <b-form-group label="Edit Trigger:">
              <b-form-radio
                v-model="editTrigger"
                value="click"
                :disabled="customEdit"
                >Click</b-form-radio
              >
              <b-form-radio
                v-model="editTrigger"
                value="dblclick"
                :disabled="customEdit"
                >Double Click</b-form-radio
              >
            </b-form-group>
            <b-form-group label="Features:">
              <b-form-checkbox v-model="enableAddRemove">
                Add/Remove rows
              </b-form-checkbox>
              <b-form-checkbox v-model="customEdit">
                Edit row with external button
              </b-form-checkbox>
              <b-form-checkbox v-model="inputValidation">
                Input validation
              </b-form-checkbox>
            </b-form-group>
          </div>
        </b-card>
        <EditableTable
          :editMode="editMode"
          :customEdit="customEdit"
          :editTrigger="editTrigger"
          :inputValidation="inputValidation"
          :enableAddRemove="enableAddRemove"
        ></EditableTable>
      </div>
    </header>
    <div>
        <b>Code Examples:</b>
        <a target="_blank" href="https://codesandbox.io/s/bootstrap-vue-editable-table-wx012?file=/src/App.vue">Edit Cell</a> |
        <a target="_blank" href="https://codesandbox.io/s/bootstrap-vue-row-editing-7w1scn?file=/src/App.vue">Edit Row</a> |
        <a target="_blank" href="https://codesandbox.io/s/vue-add-remove-table-rows-chtnj?file=/src/App.vue">Add, Update and Remove Rows</a> |
        <a target="_blank" href="https://codesandbox.io/s/vue-table-validation-pcysqz?file=/src/App.vue">Input Validation</a> |
        <a target="_blank" href="https://codesandbox.io/s/vue-table-load-data-api-cub6i">Load Data via Rest API</a>
      </div>
    <div class="footer">Made by <a target="_blank" href="https://muhimasri.com">Muhi Masri</a> with ❤️</div>
  </main>
</template>

<script>
import EditableTable from "./EditableTable";
import { BFormRadio, BCard, BFormGroup, BFormCheckbox } from "bootstrap-vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

export default {
  components: {
    EditableTable,
    BFormRadio,
    BCard,
    BFormGroup,
    BFormCheckbox,
  },
  data() {
    return {
      customEdit: false,
      editMode: "cell",
      editTrigger: "click",
      inputValidation: false,
      enableAddRemove: false,
    };
  },
  methods: {},
};
</script>

<style>
table {
    overflow-x: unset;
}
.theme-default-content:not(.custom) {
    max-width: 820px;
}
.home {
  padding: 0;
}

.home .hero img {
  max-height: 192px;
}

.home .hero h1 {
  font-size: 27px;
}

.required-description {
  color: #909090;
  margin-bottom: 14px;
}

.playground-title {
    margin: 0;
    margin-top: 10px;
    margin-bottom: 15px;
}

.card-body {
  padding: 0.2rem 0.9rem;
} 

.main-container {
  display: flex;
    align-items: center;
    flex-direction: column;
  margin: 20px;
  text-align: left;
}

table.editable-table td {
  vertical-align: middle;
}

.editable-table .data-cell {
  padding: 8px;
  vertical-align: middle;
}

.editable-table .custom-checkbox {
  width: 50px;
}

.name-col {
  width: 120px;
}

.department-col {
  width: 150px;
}

.age-col {
  width: 100px;
}

.date-col {
  width: 200px;
}

.is-active-col {
  width: 100px;
}

.config-container {
  display: flex;
  column-gap: 60px;
}
</style>