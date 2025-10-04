# vuetify-to-xlsx

NPM library for Vuetify that directly exports your v-data-table component to an Excel file.

## Installation

```bash
npm install vuetify-to-xlsx
```

or

```bash
yarn add vuetify-to-xlsx
```

## Usage

This library provides a simple way to export data from Vuetify's `v-data-table` component to an Excel file using the [xlsx](https://www.npmjs.com/package/xlsx) library.

### Basic Example

```javascript
import { exportToXlsx } from 'vuetify-to-xlsx';

// Your v-data-table headers
const headers = [
  { title: 'Name', key: 'name' },
  { title: 'Email', key: 'email' },
  { title: 'Age', key: 'age' }
];

// Your v-data-table items
const items = [
  { name: 'John Doe', email: 'john@example.com', age: 30 },
  { name: 'Jane Smith', email: 'jane@example.com', age: 25 }
];

// Export to Excel
exportToXlsx({
  headers: headers,
  items: items,
  fileName: 'my-data.xlsx',
  sheetName: 'Users'
});
```

### Vue Component Example

```vue
<template>
  <div>
    <v-data-table
      :headers="headers"
      :items="items"
    >
    </v-data-table>
    <v-btn @click="exportData">Export to Excel</v-btn>
  </div>
</template>

<script>
import { exportToXlsx } from 'vuetify-to-xlsx';

export default {
  data() {
    return {
      headers: [
        { title: 'Name', key: 'name' },
        { title: 'Email', key: 'email' },
        { title: 'Age', key: 'age' }
      ],
      items: [
        { name: 'John Doe', email: 'john@example.com', age: 30 },
        { name: 'Jane Smith', email: 'jane@example.com', age: 25 }
      ]
    };
  },
  methods: {
    exportData() {
      exportToXlsx({
        headers: this.headers,
        items: this.items,
        fileName: 'users-export.xlsx',
        sheetName: 'Users'
      });
    }
  }
};
</script>
```

## API

### exportToXlsx(options)

Exports data from v-data-table to an Excel file.

#### Parameters

- `options` (Object):
  - `headers` (Array, required): Array of header objects from v-data-table. Each header should have at least `title` and `key` properties.
  - `items` (Array, required): Array of data items from v-data-table.
  - `fileName` (String, optional): Name of the exported file. Default: `'export.xlsx'`
  - `sheetName` (String, optional): Name of the Excel sheet. Default: `'Sheet1'`

#### Returns

- `void`: The function downloads the Excel file directly to the user's browser.

## Dependencies

This library uses:
- [xlsx](https://www.npmjs.com/package/xlsx) - For Excel file generation
- [vuetify](https://vuetifyjs.com/) - Peer dependency for v-data-table compatibility

## Development Status

🚧 **Note**: This is the initial setup of the library. The core export functionality is planned for future iterations. The entry point and structure are now in place.

### Planned Features

- Extract and process v-data-table headers
- Map data items according to header configuration
- Generate Excel workbook with proper formatting
- Support for custom cell styles
- Support for multiple sheets
- Advanced filtering and sorting options

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT
