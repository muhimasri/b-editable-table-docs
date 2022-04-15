# Column Width

To set the width of any column, you can pass the `class` property in the `fields` object. This feature is part of Bootstrap Vue Table. You can learn more from [Bootstrap Table Docs](https://bootstrap-vue.org/docs/components/table).

Below is an example of how you set the width by adding a CSS class to the column:
```json
fields: [
	{ key: "name", label: "Name", type: "text", class: "name-col", editable: true, placeholder: "Enter Name..."},
	{ key: "age", label: "Age", type:"range", class: "age-col", min:"0", max:"100", editable: true, placeholder: "Enter Age..." }
]
```
```css
<style>
.name-col {
  width: 120px;
}
.age-col {
  width: 100px;
}
</style>
```