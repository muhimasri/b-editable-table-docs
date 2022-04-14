<template>
  <div class="main-container">
    <b-card bg-variant="light">
      <div v-if="inputValidation">
        <i>* Name is required</i> | <i>* Must select a department</i> |
        <i>* Must be 19 or older</i>
      </div>
      <div class="config-container">
        <b-form-group label="Edit Mode:">
          <b-form-radio v-model="editMode" value="cell" :disabled="customEdit"
            >Cell</b-form-radio
          >
          <b-form-radio v-model="editMode" value="row" :disabled="customEdit"
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
        <div>
          <b-checkbox v-model="enableAddRemove"> Add/Remove rows </b-checkbox>
          <b-checkbox v-model="customEdit">
            Edit row with external button
          </b-checkbox>
          <b-checkbox v-model="inputValidation"> Input validation </b-checkbox>
        </div>
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
</template>

<script>
import EditableTable from "./EditableTable";

export default {
  components: {
    EditableTable,
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
.main-container {
  margin: 20px;
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
  align-items: center;
  column-gap: 25px;
}
</style>