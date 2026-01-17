# Parse The FIX

[Parse The FIX](https://parsethefix.com)
 is a browser-based FIX message parser and dashboard built in TypeScript for inspecting, filtering, and comparing FIX messages. 
It keeps everything in-session (no messages are stored or sent anywhere) and gives you multiple widgets to analyze messages as a split-view table and timeline.

<img width="1896" height="893" alt="image" src="https://github.com/user-attachments/assets/e9d274dc-05b3-4ad0-b7fe-eb68037f9a24" />

## App Layout

- **Header**: Theme toggle.
- **Sidebar**: Dashboard list and dashboard actions.
- **Main Canvas**: Drag-and-drop widgets per dashboard.

Widgets are draggable/resizable on desktop; on smaller screens they snap into a single-column layout.

## Parsing FIX Messages

1. In **Enter FIX Messages**, paste raw FIX logs or messages.
2. Click **Process** to parse and load messages into the table and timeline widgets.
3. Use **Sample Data** to see a full demo instantly.
4. Click **Clear** to reset the dashboard’s message state.

### Supported Input Formats

The parser accepts common FIX delimiters and normalizes them automatically when **Auto Format** is enabled (default):

- SOH (`0x01`)
- `^A`
- Pipes (`|`)

It also cleans up unformatted FIX logs, handling line breaks and rebuilding tag/value pairs before parsing.

### Filters (inline)

Use the filter icon next to **Sample Data** to narrow down parsed messages by tag/value content:

- Enter comma-separated filters (up to 5 tokens).
- Example: `35=8,FILLED`
- Filters match tags, values, and value descriptions.

## Widgets

### Enter FIX Messages

This widget controls how parsing happens and drives the rest of the dashboard.

#### Settings (gear icon)

- **Auto Format**: Normalize delimiters and reformat messages for readability (enabled by default).
- **Order by Timestamp**: Sort messages by tag `52` (SendingTime).
- **Remove Heartbeats**: Exclude selected message types (default includes `0`). Use **Edit** to manage the list.

### FIX Messages Table

Displays parsed messages as tag/value rows. It supports single-message view or side-by-side comparisons.

#### Settings

- **Split Table View**: Compare message pairs side-by-side.
- **Highlight Differences**: Emphasize tag value mismatches when split view is on.
- **Line up Tags**: Align tag rows across both sides (disabled when Compare By is active).
- **Compare By**: Group and compare by `Order ID (11)`, `Side (54)`, or `Symbol (55)`.
- **Remove Common Fields**: Hide repetitive tags (default `8`, `9`). Use **Edit** to customize.

### FIX Messages Timeline

Shows a time-ordered timeline of key message details.

- Click a timeline row to sync the table view to that message.
- Messages are color-coded by type and show sender/target, type, and a summary detail.

## Dashboards

Dashboards let you keep multiple layouts or message sets open at once.

- Use the sidebar **Dashboard** icon to view and manage dashboards.
- Click **+** to add a dashboard (up to 12).
- Click the pencil to rename a dashboard.
- Click **–** to remove a dashboard.

Each dashboard stores its own widget layout and parsing state.

## Tips

- Use **Sample Data** before pasting real logs to see the full flow.
- Turn on **Order by Timestamp** if log entries arrive out of order.
- Use **Remove Common Fields** to focus on tag changes while comparing.
