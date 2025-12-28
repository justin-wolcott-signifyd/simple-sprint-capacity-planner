# Simple Sprint Capacity Planner

A lightweight, browser-based sprint planning tool that visualizes team capacity and task assignments on a Gantt-style chart. No backend, no accounts, no dependencies - just a single HTML file that runs entirely in your browser.

Live demo: https://justin-wolcott-signifyd.github.io/simple-sprint-capacity-planner/

## Why This Exists

Most sprint planning happens in Jira, Linear, or similar tools - but those tools are optimized for backlog management, not capacity visualization. During sprint planning meetings, teams often struggle to answer simple questions like:

- Is anyone overloaded this sprint?
- Do we have room for one more ticket?
- What happens to the schedule if someone is out Thursday/Friday?

This tool provides a visual, drag-and-drop interface specifically designed to answer those questions in real-time during planning sessions.

## Features

### Core Functionality

- **Gantt-style visualization**: See all team members and their assigned work across the sprint timeline
- **Drag-and-drop scheduling**: Move tasks from the backlog to team members, or between team members
- **Multi-select**: Shift-click or Ctrl-click to select multiple backlog items and assign them all at once
- **Resize tasks**: Drag the right edge of any task bar to adjust its duration
- **Automatic weekend handling**: Tasks automatically extend across weekends (a 3-day task starting Friday ends Wednesday, not Sunday)
- **Holiday support**: Click any date header to mark it as a holiday - tasks will extend around it just like weekends

### Task Status Tracking

Tasks have three statuses with distinct visual colors:
- **Dev** (pink): In development
- **QA** (yellow): Ready for or in QA
- **Done** (green): Completed

The "done" row at the bottom serves as a completion bucket. Dragging a task there automatically marks it done; dragging it back out reverts it to dev status.

### Data Management

- **Automatic save**: All changes save to browser localStorage automatically
- **JSON export/import**: Copy the full state as JSON to share with teammates or back up your plan. Paste and click Load to restore.
- **No server required**: Everything runs client-side. Your data never leaves your browser.

## How to Use It

### Initial Setup

1. Set the sprint start date (defaults to next Monday)
2. Set the number of working days (default 10 for a two-week sprint)
3. Add team members using the "+ Person" button

### During Sprint Planning

1. Add tickets to the backlog (paste ticket IDs like "PROJ-123")
2. Drag tickets from the backlog onto team members' rows at the appropriate start date
3. Resize tasks by dragging their right edge to set duration
4. Click any task to edit its details (name, start date, duration, status)
5. Mark holidays by clicking date headers (company holidays, PTO days, etc.)

### During the Sprint

The tool works well as a stand-up driver:

1. Open the planner on a shared screen
2. Walk through each team member's row from left to right
3. The "today" column is highlighted in blue - easy to see where everyone should be
4. As work completes, drag tasks to the "done" row or update their status
5. If scope changes, drag tasks around to rebalance

The visual nature makes blockers and overallocation immediately obvious. If someone's row is packed while another's is empty, the imbalance is hard to miss.

### Saving and Sharing Plans

The JSON state at the bottom of the page contains everything:
- Sprint configuration
- All team members
- All tasks with their assignments, durations, and statuses
- Holiday dates

To share a plan:
1. Click "Copy" to copy the JSON to your clipboard
2. Share via Slack, email, or paste into a shared doc
3. Recipients paste the JSON into the textarea and click "Load"

To back up before making changes:
1. Copy the JSON
2. Make your changes
3. If needed, paste the old JSON and Load to revert

## Keyboard Shortcuts

- **Escape**: Close any open modal, or clear the current selection

## Limitations

- No real-time collaboration (it's a single HTML file)
- No integration with Jira/Linear/etc.
- Data lives in browser localStorage - clearing browser data clears your plan
- No undo/redo (use JSON export as a manual checkpoint)

## Running Locally

Download the HTML file and open it in any modern browser. That's it.

## Self-Hosting

Upload the HTML file (renamed to `index.html`) to any static hosting:
- GitHub Pages
- Netlify
- Vercel
- S3 with static hosting
- Any web server

No build step required.