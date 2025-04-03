# Developer Utilities Dashboard

A collection of handy web-based utility tools for developers, built with static HTML, Tailwind CSS (via CDN), and vanilla JavaScript. This dashboard provides quick access to common tasks without needing external websites or complex installations.

## Features / Included Tools

This dashboard currently includes the following tools:

*   **Base64 Converter:** Encode text to Base64 and decode Base64 strings back to text.
*   **URL Encoder / Decoder:** Encode/decode strings for safe use within URLs according to RFC 3986.
*   **JWT Decoder:** Decode the Header and Payload parts of a JSON Web Token (JWT) for inspection. *(Note: Does not verify the signature).*
*   **UNIX Timestamp Converter:** Convert between Unix timestamps (seconds since epoch) and human-readable dates (local and UTC). Includes a "Get Current Timestamp" feature.
*   **Color Visualizer:** Convert between HEX, RGB, and HSL color formats with a live preview and color picker.
*   **Markdown Previewer:** Render Markdown text into an HTML preview in real-time using `marked.js`.
*   **UUID Generator:** Generate cryptographically strong Version 4 UUIDs using the browser's `crypto.randomUUID` (with a basic fallback).
*   **Char-Word Counter:** Count characters, words (based on simple whitespace splitting), and lines in a given text block.
*   **REGEX Tester:** Test JavaScript-compatible regular expressions against sample text and view the list of matches found.
*   **JSON Validator & Formatter:** Validate JSON structure and pretty-print valid JSON with selectable indentation (spaces or tabs).
*   **CSV Converter & Viewer:** Convert simple CSV data into a JSON array of objects and display the data in an HTML table.
*   **Binary Text Converter:** Convert text to its 8-bit binary representation (space-separated bytes) and vice-versa.
*   **Hash Generator:** Generate SHA-1, SHA-256, and SHA-512 hashes for input text using the browser's `SubtleCrypto` API. *(Note: MD5 generation requires adding an external library like blueimp-md5 via CDN).*
*   **Scientific Calculator:** A basic calculator supporting arithmetic operations and some scientific functions. *(Note: Uses `eval` for simplicity, which is generally unsafe and may not handle complex order of operations correctly. Primarily a demonstration).*
*   **Data Visualizer (Charts):** Create simple Bar, Line, Pie, Doughnut, Polar Area, or Radar charts from basic CSV data (label,value per line) using `Chart.js`.

## How to Use

1.  **Download/Clone:** Get all the `.html` files.
2.  **Organize:** Place all `.html` files in the **same folder** on your computer.
3.  **Open:** Open the `dashboard.html` file directly in your web browser (e.g., Chrome, Firefox, Edge).

That's it! Click on the cards in the dashboard to navigate to the individual tool pages.

## Features

*   **Search:** Filter the tools on the dashboard by name or description.
*   **Usage-Based Sorting:** Tools on the dashboard are automatically sorted based on how often you click them (most used first).
    *   **Mechanism:** Uses the browser's `localStorage` to track click counts.
    *   **Limitations:** Counts are specific to the browser you use and will be reset if you clear your browser's site data for `file:///` paths or the specific domain if hosted.
    *   **Reset:** A "[Clear Usage Counts]" button is available in the footer for testing or resetting the order.

## Dependencies

These tools rely on external libraries loaded via CDN for certain functionalities:

*   **Tailwind CSS (CDN):** Used for all styling across pages. Requires an internet connection for initial load.
*   **`jsdifflib` (CDN):** Used by the (currently unlisted) Text Difference tool for generating side-by-side diffs.
*   **`Chart.js` (CDN):** Used by the Data Visualizer tool to render charts.
*   **`marked.js` (CDN):** Used by the Markdown Previewer tool to parse Markdown.
*   **`DOMPurify` (CDN - Optional):** Recommended for enhanced security in the Markdown Previewer.
*   **(Optional) `blueimp-md5` (CDN):** Required by the Hash Generator tool *if* you need MD5 hashing (the CDN link is commented out by default in `hash_generator.html`).

## Adding New Tools

1.  Create a new `.html` file for your tool (e.g., `new_tool.html`).
2.  Use the existing tool pages as a template: include the Tailwind CDN, header with a backlink, main content area, and footer.
3.  Implement the tool's functionality using HTML, CSS (Tailwind classes), and vanilla JavaScript.
4.  Open `dashboard.html`.
5.  Add a new `<a>` card element inside the `div#tools-grid`. Ensure it includes:
    *   The `tool-card` class.
    *   A correct `href` attribute pointing to your new HTML file.
    *   `data-tool-id="uniqueToolId"` (e.g., `data-tool-id="newTool"`).
    *   `data-tool-name="Tool Display Name"`.
    *   `data-tool-desc="Brief description of the tool."`.
    *   Inner `<h3>` and `<p>` with the display name and description (add `pointer-events-none` to these inner elements).
6.  The dashboard's JavaScript should automatically pick up the new card for searching and sorting on the next page load.

## Potential Improvements

*   **Error Handling:** Enhance error handling in various tools for edge cases.
*   **Calculator Logic:** Replace the `eval`-based calculator logic with a proper expression parser (e.g., using Shunting-yard algorithm or a dedicated library) for safety and correctness.
*   **Complex Tool Features:** Add more options and capabilities to tools like the Chart Visualizer, Form Builder (if added), CSV parser (handling quotes/escapes), etc.
*   **Build Step:** For better performance and reliability (avoiding CDN issues), set up a simple build process (e.g., using Vite or Parcel) to bundle Tailwind CSS and JavaScript libraries.
*   **State Management:** For more complex interactions, consider a lightweight state management approach if the project grows significantly.
*   **UI/UX:** Improve the visual design and user experience further.