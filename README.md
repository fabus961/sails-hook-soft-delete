# Sails hook soft delete

This hook add soft delete functionality to Waterline ORM

## Installation

```shell
npm install --save sails-hook-soft-delete
```

```shell
# For yarn users
yarn add sails-hook-soft-delete
```

## Usage

### Setting up the model.js file
```javascript
 attributes: {
    created_at: { type: 'number', autoCreatedAt: true, columnName: 'created_at'},
    updated_at: { type: 'number', autoUpdatedAt: true, columnName: 'updated_at'},
    deleted_at: { type: 'ref', defaultsTo: null, columnName: 'deleted_at'},
    id: { type: 'number', autoIncrement: true, columnName: 'id'},
    }
```

### Deleting record

Now the `Model.destroyOne()` method will mark the record as soft-deleted. It set the deletedAt attribute to current date.

If you want to completely remove a record, use the `Model.forceDestroyOne()`method.

You can also use `Model.destroy()` and `Model.forceDestroy()` to soft-delete/delete many record.

### Restoring record

Once a record is soft-deleted, you can restore it using `Model.restoreOne()` /  `Method.restore()` method.

### Quering records

`Model.find()` / `Model.findOne()` will now find record which are not soft-deleted.

If you want to include soft-deleted record, use `Model.findWithTrashed()` method

To get only soft-deleted record, use `Model.findTrashed()` method


