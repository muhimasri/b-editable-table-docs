<template>
  <div class="table-container">
    <b-button v-if="enableAddRemove" variant="success" @click="handleAdd()"
      >Add Row</b-button
    >
    <b-editable-table
      :disableDefaultEdit="disableDefaultEdit"
      :rowUpdate="rowUpdate"
      :editMode="editModeValue"
      :editTrigger="editTrigger"
      class="editable-table"
      v-model="items"
      :fields="tableFields"
    >
      <template #cell(isActive)="data">
        <span v-if="data.value">Yes</span>
        <span v-else>No</span>
      </template>
      <template #cell(edit)="data">
        <div class="edit-cell" v-if="data.isEdit">
          <BIconX class="edit-icon" @click="handleSubmit(data, false)"></BIconX>
          <BIconCheck2
            class="edit-icon check-icon"
            @click="handleSubmit(data, true)"
          ></BIconCheck2>
        </div>
        <BIconPencil
          v-else
          class="edit-icon"
          @click="handleEdit(data, true)"
        ></BIconPencil>
      </template>
      <template #cell(delete)="data">
        <BIconTrash
          class="remove-icon"
          @click="handleDelete(data)"
        ></BIconTrash>
      </template>
    </b-editable-table>
  </div>
</template>

<script>
import BEditableTable from "bootstrap-vue-editable-table";
import {
  BIconTrash,
  BIconPencil,
  BIconX,
  BIconCheck2,
  BButton,
} from "bootstrap-vue";
export default {
  components: {
    BEditableTable,
    BIconX,
    BIconTrash,
    BIconPencil,
    BIconCheck2,
    BButton,
  },
  props: {
    editMode: {
      default: "cell",
    },
    customEdit: {
      default: false,
    },
    editTrigger: {
      default: "click",
    },
    inputValidation: {
      default: false,
    },
    enableAddRemove: {
      default: false,
    },
  },
  computed: {
    tableFields() {
      let newFields = [];
      const hideColumns = {
        edit: !this.customEdit,
        delete: !this.enableAddRemove,
      };
      newFields = this.fields.filter((item) => !hideColumns[item.key]);
      return newFields;
    },
    editModeValue() {
      if (this.customEdit) {
        return "row";
      }
      return this.editMode;
    },
    disableDefaultEdit() {
      if (this.customEdit) {
        return true;
      }
      return false;
    },
  },
  data() {
    return {
      fields: [
        { key: "delete", label: "" },
        {
          key: "name",
          label: "Name",
          type: "text",
          editable: true,
          placeholder: "Enter Name...",
          class: "name-col",
          validate: this.validateName,
        },
        {
          key: "department",
          label: "Department",
          type: "select",
          editable: true,
          class: "department-col",
          options: [
            { value: 0, text: "Select a department..." },
            { value: 1, text: "HR" },
            { value: 2, text: "Engineer" },
            { value: 3, text: "VP" },
            { value: 4, text: "CEO" },
          ],
          validate: this.validateSelect,
        },
        {
          key: "dateOfBirth",
          label: "Date Of Birth",
          type: "date",
          editable: true,
          class: "date-col",
          locale: "en",
          "date-format-options": {
            year: "numeric",
            month: "numeric",
            day: "numeric",
          },
          validate: this.validateDate,
        },
        {
          key: "isActive",
          label: "Active",
          type: "checkbox",
          editable: true,
          class: "is-active-col",
        },
        { key: "edit", label: "", class: "edit-col" },
      ],
      items: [
        {
          id: 1,
          name: "Dickerson",
          department: 1,
          dateOfBirth: "1984-05-20",
          isActive: true,
        },
        {
          id: 2,
          name: "Larsen",
          department: 2,
          dateOfBirth: "1972-07-25",
          isActive: false,
        },
        {
          id: 3,
          name: "Geneva",
          department: 3,
          dateOfBirth: "1981-02-02",
          isActive: false,
        },
        {
          id: 4,
          name: "Jami",
          department: 4,
          dateOfBirth: "1964-10-19",
          isActive: true,
        },
      ],
      rowUpdate: {},
    };
  },
  methods: {
    handleAdd() {
      const newId = Date.now();
      this.rowUpdate = {
        edit: true,
        id: newId,
        action: "add",
        data: {
          id: newId,
          age: null,
          name: "",
          department: 1,
          dateOfBirth: null,
          isActive: false,
        },
      };
    },
    handleSubmit(data, update) {
      this.rowUpdate = {
        edit: false,
        id: data.id,
        action: update ? "update" : "cancel",
      };
    },
    handleEdit(data) {
      this.rowUpdate = { edit: true, id: data.id };
    },
    handleDelete(data) {
      this.rowUpdate = { id: data.id, action: "delete" };
    },
    validateName(value) {
      if (this.inputValidation) {
        if (value === "") {
          return {
            valid: false,
            errorMessage: "Please enter name",
          };
        }
        return { valid: true };
      }
    },
    validateDate(value) {
      if (this.inputValidation) {
        const year = new Date(value).getFullYear();
        if (year > 2003) {
          return {
            valid: false,
            errorMessage: "Must be 19 or older",
          };
        }
        return { valid: true };
      }
    },
    validateSelect(value, options) {
      if (this.inputValidation) {
        if (value === 0) {
          return {
            valid: false,
            errorMessage: "Please select a department",
          };
        }
        return { valid: true };
      }
    },
  },
};
</script>

<style>
.table-container {
  margin: 10px;
}

table.editable-table {
  margin-top: 10px;
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

.remove-icon {
  color: red;
  cursor: pointer;
  font-size: 20px;
}

.edit-icon {
  color: rgb(4, 83, 158);
  cursor: pointer;
  font-size: 20px;
}

.check-icon {
  color: #36c700;
  margin-left: 7px;
}

.edit-cell {
  display: flex;  
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
  width: 78px;
  margin-left: 9px;
}

.edit-col {
  width: 60px;
}
</style>