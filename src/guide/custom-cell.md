# Custom Cell
To customize a none editable cell, you can use Bootstraps' scoped slots.

**Example rendering a `boolean` field to `Yes` or `No` value:**

```javascript
<b-editable-table v-model="items" :fields="fields">
	<template #cell(isActive)="data">
        <span v-if="data.value">Yes</span>
        <span v-else>No</span>
     </template>
</b-editable-table>
```
For more details about custom slots, please read [BootstrapVue Table documentation](https://bootstrap-vue.org/docs/components/table) 