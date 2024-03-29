# Load Data via REST API
[Run example on CodeSandbox](https://codesandbox.io/s/vue-table-load-data-api-cub6i)
```html
<template>
<div>
    <b-editable-table :busy="loading" bordered class="editable-table" v-model="users" :fields="fields">
      <template #cell-isActive="data">
        <span v-if="data.value">Yes</span>
        <span v-else>No</span>
      </template>
      <template #table-busy>
        <div class="text-center text-danger my-2">
          <b-spinner class="align-middle"></b-spinner>
          <strong>Loading...</strong>
        </div>
      </template>
    </b-editable-table>
</div>
</template>

<script>
import BEditableTable from 'bootstrap-vue-editable-table';
import {BSpinner} from 'bootstrap-vue';
export default {
  components: {
    BEditableTable,
    BSpinner
  },
  data() {
    return {
      fields: [
        {id: 1, key: "name", label: "Name", type: "text", editable: true },
        {id: 2, key: "email", label: "Email", type: "email", editable: true },
        {id: 3, key: "phone", label: "Phone", type: "text", editable: true }
      ],
      users: [],
      loading: false
    };
  },
  async mounted() {
    this.loading = true;
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const users = await response.json();
    this.users = users;
    this.loading = false;
  }
};
</script>

<style>
table.editable-table {
  margin: auto;
  width: auto;
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
  width: 100px
}
</style>

</style>

```
