# Data Binding

|Data | Binding |
|--|--|
| :items="items" | One-way binding
| v-model="items" | Two-way binding

When using `v-model` the data will be updated automatically:

`<b-editable-table v-model="items" :fields="fields"></b-editable-table>`

Otherwise, using `:items` prop to pass data will require updating the data manually on input change:

[Run example on CodeSandbox](https://codesandbox.io/s/vue-table-one-way-binding-ug039)
```html
<template>
<div>
    <b-editable-table bordered class="editable-table" :items="items" :fields="fields" @input-change="handleInput">
    </b-editable-table>
</div>
</template>

<script>
import BEditableTable from 'bootstrap-vue-editable-table';
export default {
  components: {
    BEditableTable
  },
  data() {
    return {
      fields: [
        { key: "name", label: "Name", type: "text", editable: true, placeholder: "Enter Name...", class: "name-col"},
        { key: "department", label: "Department", type: "select", editable: true, class: "department-col" , options: [
          { value: 1, text: 'HR' },
          { value: 2, text: 'Engineer' },
          { value: 3, text: 'VP' },
          { value: 4, text: 'CEO'}
        ]},
        { key: "age", label: "Age", type:"range", min:"0", max:"100", editable: true, placeholder: "Enter Age...", class: "age-col" },
        { key: "dateOfBirth", label: "Date Of Birth", type: "date", editable: true, class: "date-col", locale: "en",
          "date-format-options": {
            year: "numeric",
            month: "numeric",
            day: "numeric",
          }, },
        { key: "isActive", label: "Is Active", type: "checkbox", editable: true, class: "is-active-col" }
      ],
       items: [
          { id:1, age: 40, name: 'Dickerson', department: 1, dateOfBirth: '1984-05-20', isActive: true },
          { id:2, age: 21, name: 'Larsen', department: 2, dateOfBirth: '1972-07-25', isActive: false },
          { id:3, age: 89, name: 'Geneva', department: 3, dateOfBirth: '1981-02-02', isActive: false },
          { id:4, age: 38, name: 'Jami', department: 4, dateOfBirth: '1964-10-19', isActive: true },
        ]
    };
  },
  methods: {
      handleInput(data) {
        const updatedRow = {...this.items[data.index], [data.field.key]: data.value};
        this.$set(this.items, data.index, updatedRow);
      }
  }
};
</script>
```