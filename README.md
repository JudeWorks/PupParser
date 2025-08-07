# PupParser

PupParser is a specialized, in-browser CSV (Comma-Separated Values) editor designed to make data entry for specific applications easy and error-free. Instead of a generic spreadsheet, it provides a tailored user interface with context-aware inputs like dropdowns, date pickers, and format validation, ensuring the generated CSV data conforms to predefined schemas.

The entire application runs locally in your web browser. No data is ever sent to a server.

## Key Features

-   **Create or Load CSVs**: Start with a fresh template for a known app or paste in existing CSV data to edit.
-   **Dynamic Editable Table**: Data is rendered in a clean, interactive table where every cell is an appropriate input field.
-   **Context-Aware Inputs**: The tool intelligently provides the best input type for the data:
    -   **Dropdowns** for predefined choices (e.g., `type`, `Cache`, `Pinned`).
    -   **Date Pickers** for calendar dates.
    -   **Guided Time Selectors** for 24-hour time formats.
    -   **Validated Inputs** for specific formats (e.g., URL paths, numeric-only fields).
    -   **"Test Link"** helpers for all URL fields.
-   **Real-time CSV Output**: Any change made in the table is instantly reflected in the raw CSV output box.
-   **PickPup Spec Management**:
    -   Dynamically add new `SpecGroup:SpecDetail` columns.
    -   Toggle the visibility of entire column groups to focus on the data you need.
-   **Data Safety**: The app will warn you before you navigate away or close the tab if you have unsaved changes.
-   **Easy Exporting**:
    -   **Copy CSV**: Copies the raw CSV output to your clipboard.
    -   **Download CSV**: Downloads the data as a `.csv` file, intelligently named with the current date, time, and app name (e.g., `2023-11-28_1545-PupKit.csv`).

## How to Use

1.  **Open the File**: Simply open the `PupParser.html` file in any modern web browser.

2.  **Getting Started**: You have two options:
    -   **Create New**: Select an application (e.g., "PupKit", "PupCast") from the **Create New** dropdown. This will generate a blank table with the correct headers for that app.
    -   **Load Existing**: Paste your raw CSV text into the **Paste CSV to Load** text area and click the **Load CSV** button.

3.  **Editing Data**:
    -   Click into any cell in the table to edit its content.
    -   Use the specialized controls like date pickers and dropdowns to ensure your data is correctly formatted.

4.  **Managing Rows & Columns**:
    -   Click the **Add Row** button at the bottom of the table to add a new, empty row.
    -   Click the **Delete** button at the end of any row to remove it.
    -   If you are working with a **PickPup** file, you can add new specification columns using the **Add Column** controls.

5.  **Filtering Columns (PickPup only)**:
    -   When a PickPup file is loaded, a list of checkboxes for each `SpecGroup` will appear.
    -   Uncheck a box to hide all columns belonging to that group.
    -   Use the **Check All** and **Uncheck All** buttons for quick filtering.

6.  **Exporting Your Data**:
    -   Click **Copy CSV** to copy the contents of the **Raw CSV Output** box.
    -   Click **Download CSV** to save your work as a `.csv` file. This is considered a "save" action and will reset the "unsaved changes" warning.

## App-Specific Rules & Headers

The power of PupParser comes from its enforcement of app-specific rules. Here are the details for each app, including their required header format.

### PickPup
-   **Column Format**: Supports flexible columns in the `SpecGroup:SpecDetail` format (e.g., `Color:Red`).
-   **Special Features**: This is the only app type that enables the "Add Column" controls and the "Spec Groups" visibility toggles.

**Header:**
```csv
ItemName,HeroPhotoURL,Photo2URL,Photo3URL,Photo4URL,Photo5URL,Video1URL,Category1,Category2,Category3
