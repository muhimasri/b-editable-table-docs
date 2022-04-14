# API
### Events:
|Event |Arguments | Description |
|--|--|--|
| input-change &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | `data` - The same object returned by Bootstrap with additional `id` property and the current changed `value` | Emitted when any input value changes

### Properties:
|Property |Options| Default | Description |
|--|--|--|--|
| editMode |`cell` - Edit one cell <br/> `row` - Edit all the cells of a row at once| `cell`| Change edit mode
| editTrigger|`click` - Edit on mouse click <br/> `dblclick` - Edit on mouse double click| `click`| Change edit trigger
| disableDefaultEdit|`true` - Disable default edit behavior. This is useful when wanting to change the edit manually through an external button <br/> `false` - Keep default edit behavior. This will make the cell editable as soon as clicking on the `cell` or `row`| `false`| Turn off default edit behavior
| rowUpdate | | | Update a specified row. [Please refer to this section for usage example](#add-update-and-remove-rows) 