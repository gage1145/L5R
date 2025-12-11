<%*
const title = tp.file.title;
let sessionNumber;
let previous;
if (title.startsWith("Untitled")) {
	sessionNumber = await tp.system.prompt("Enter Session Number");
	await tp.file.rename("Session " + sessionNumber);
	previous = parseInt(sessionNumber) - 1
}
-%>
---
date: <% tp.date.now("YYYY-MM-DD") %>
session: <% sessionNumber %>
previous:  "[[Session <% previous %>]]"
summary:
---
## Characters
- **Name**

## Overview
Brief session overview.

## Key Learnings
- Description of any important information that the party learned.

## Who Did We Meet?
**Name.** Description

## Items Oat Worked
- Small description.Worked
- Small description.