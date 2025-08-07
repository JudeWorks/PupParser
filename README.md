# PupParser

PupParser is a specialized, in-browser CSV (Comma-Separated Values) editor designed to make data entry for specific applications easy and error-free. Instead of a generic spreadsheet, it provides a tailored user interface with context-aware inputs like dropdowns, date pickers, and format validation, ensuring the generated CSV data conforms to predefined schemas.

> **Note**: The entire application runs locally in your web browser. No data is ever sent to a server.

---

## Key Features

- **Create or Load CSVs**\
  Start with a fresh template for a known app or paste in existing CSV data to edit.

- **Dynamic Editable Table**\
  Data is rendered in a clean, interactive table where every cell is an appropriate input field.

- **Context-Aware Inputs**\
  The tool intelligently provides the best input type for the data:

  - Dropdowns for predefined choices (e.g., `type`, `Cache`, `Pinned`)
  - Date Pickers for calendar dates
  - Guided Time Selectors for 24-hour time formats
  - Validated Inputs for specific formats (e.g., URL paths, numeric-only fields)
  - "Test Link" helpers for all URL fields

- **Real-time CSV Output**\
  Any change made in the table is instantly reflected in the raw CSV output box.

- **PickPup Spec Management**

  - Dynamically add new `SpecGroup:SpecDetail` columns
  - Toggle the visibility of entire column groups to focus on the data you need

- **Data Safety**

  - The app warns you before navigating away or closing the tab if you have unsaved changes

- **Easy Exporting**

  - `Copy CSV`: Copies the raw CSV output to your clipboard
  - `Download CSV`: Downloads the data as a `.csv` file with an intelligent name\
    *(e.g., **`2023-11-28_1545-PupKit.csv`**)*

---

## How to Use

### 1. Open the File

Open the `PupParser.html` file in any modern web browser.

### 2. Getting Started

You have two options:

- **Create New**\
  Select an application (e.g., `PupKit`, `PupCast`) from the *Create New* dropdown.
- **Load Existing**\
  Paste raw CSV text into the *Paste CSV to Load* text area and click `Load CSV`.

### 3. Editing Data

- Click into any cell in the table to edit its content.
- Use the specialized controls like date pickers and dropdowns for correct formatting.

### 4. Managing Rows & Columns

- `Add Row` button → adds a new, empty row.
- `Delete` button (end of row) → removes the row.
- For PickPup:
  - Use `Add Column` controls to add spec columns.

### 5. Filtering Columns (PickPup Only)

- Checkboxes for each `SpecGroup` appear when a PickPup file is loaded.
- Uncheck to hide entire groups.
- Use `Check All` / `Uncheck All` for quick filtering.

### 6. Exporting Your Data

- `Copy CSV` → copies the raw CSV output.
- `Download CSV` → saves your data as a `.csv` file and resets the "unsaved changes" warning.

---

## App-Specific Rules & Headers

PupParser enforces strict app-specific formats. Below are the rules and header requirements:

---

### PickPup

- **Column Format**:\
  `SpecGroup:SpecDetail` (e.g., `Color:Red`)
- **Special Features**:
  - Enables `Add Column` controls
  - Enables `Spec Groups` visibility toggles

**Header**:

```csv
ItemName,HeroPhotoURL,Photo2URL,Photo3URL,Photo4URL,Photo5URL,Video1URL,Category1,Category2,Category3
```

---

### PupCast

- `type`: Dropdown (`photo`, `video`)
- `duration`: Numeric-only
- `start_date`, `end_date`: Date picker → `YYYY-MM-DD`
- `start_time`, `end_time`:
  - Dropdowns for `Hour (00–23)` and `Minute (00–59)`
  - Displayed in 24-hour format with `PST` notice

**Header**:

```csv
type,name,url,duration,trigger,start_date,end_date,start_time,end_time
```

---

### PupKit

- `location`: Text field that enforces leading `/`
- `dateChanged`: Date picker → `MM-DD-YYYY`
- `Cache`, `Pinned`: Dropdown (`yes`, `no`)

**Header**:

```csv
name,location,url,dateChanged,Cache,Pinned,category,subcategory,tags
```

---

### WildStream

- `Type`: Dropdown (`photo`, `video`)
- `DisplayDuration`: Numeric-only (only shown if `Type` is `photo`)

**Header**:

```csv
Title,URL,Description,Type,DisplayDuration
```

---

## Technical Overview

- **Stack**:\
  Built with **vanilla HTML, CSS, and JavaScript** (no frameworks)

- **Dependencies**:\
  Uses `PapaParse.js` for client-side CSV parsing

- **Structure**:

  - Application logic is encapsulated in an **IIFE (Immediately Invoked Function Expression)** to avoid polluting the global scope
  - Organized into clear functions for:
    - Rendering
    - Data manipulation
    - Event handling

