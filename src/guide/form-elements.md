# Form Elements
Every column requires a `type` and `editable` property to make the cell editable:

```json
[
  { key: "name", label: "Name", type: "text", editable: true},
  { key: "department", label: "Department", type: "select", options: ['Accounting', 'Marketing', 'Development', 'HR'], editable: true },
  { key: "age", label: "Age", type: "number", editable: true },
  { key: "dateOfBirth", label: "Date Of Birth", type: "date", editable: true },
  { key: "isActive", label: "Is Active", type: "checkbox", editable: true },
]
```
Elements' attributes and properties are supported by passing them directly through the `field` object. For example, you can add `size` and `locale` props to the date picker as follows:
```
{ key:  "dateOfBirth", label:  "Date Of Birth", size:"lg", locale:"fr", type: "date", editable: true }
```
**Supported Bootstrap form elements:**
|Type | Description |
|--|--|
| text | Bootstrap Form Text Input
| textarea | Bootstrap Form Textarea
| number | Bootstrap Form Number Input
| select | Bootstrap Form Select
| date | Bootstrap Form Datepicker
| checkbox | Bootstrap Form Checkbox
| rating | Bootstrap Form Rating