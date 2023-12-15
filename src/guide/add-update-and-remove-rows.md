# Add, Update and Remove Rows
To add, update and remove rows using external buttons, you need to pass the `rowUpdate` prop containing the row id and other required information. Below is a full example:

[Run example on CodeSandbox](https://codesandbox.io/s/vue-add-remove-table-rows-chtnj)
```html
<template>
  <div class="table-container">
    <b-button variant="success" @click="handleAdd()">Add</b-button>
    <b-editable-table
      disableDefaultEdit
      :rowUpdate="rowUpdate"
      :editMode="'row'"
      bordered
      class="editable-table"
      v-model="items"
      :fields="fields"
    >
      <template #cell(isActive)="data">
        <span v-if="data.value">Yes</span>
        <span v-else>No</span>
      </template>
      <template #cell(edit)="data">
        <div v-if="data.isEdit">
          <BIconX class="edit-icon" @click="handleSubmit(data, false)"></BIconX>
          <BIconCheck
            class="edit-icon"
            @click="handleSubmit(data, true)"
          ></BIconCheck>
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
  BIconCheck,
  BButton,
} from "bootstrap-vue";
export default {
  components: {
    BEditableTable,
    BIconX,
    BIconTrash,
    BIconPencil,
    BIconCheck,
    BButton,
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
        },
        {
          key: "department",
          label: "Department",
          type: "select",
          editable: true,
          class: "department-col",
          options: [
            { value: 1, text: "HR" },
            { value: 2, text: "Engineer" },
            { value: 3, text: "VP" },
            { value: 4, text: "CEO" },
          ],
        },
        {
          key: "age",
          label: "Age",
          type:"range", min:"0", max:"100",
          editable: true,
          placeholder: "Enter Age...",
          class: "age-col",
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
        },
        {
          key: "isActive",
          label: "Is Active",
          type: "checkbox",
          editable: true,
          class: "is-active-col",
        },
        { key: "edit", label: "" },
      ],
      items: [
        {
          id: 1,
          age: 40,
          name: "Dickerson",
          department: 1,
          dateOfBirth: "1984-05-20",
          isActive: true,
        },
        {
          id: 2,
          age: 21,
          name: "Larsen",
          department: 2,
          dateOfBirth: "1972-07-25",
          isActive: false,
        },
        {
          id: 3,
          age: 89,
          name: "Geneva",
          department: 3,
          dateOfBirth: "1981-02-02",
          isActive: false,
        },
        {
          id: 4,
          age: 38,
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
      this.rowUpdate = {
        edit: true,
        id: Date.now(),
        action: "add",
        // The default add position is at the top of the list. Use the below prop to insert a new row to the very end.
        // addPosition: "end",
        data: {
          id: Date.now(),
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
    }
  },
};
</script>

<style>
.table-container {
  margin: 10px;
  width: auto;
}

table.editable-table {
  margin-top: 10px;
}

table.editable-table td {
  vertical-align: middle;
  padding: 0;
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
</style>
```
