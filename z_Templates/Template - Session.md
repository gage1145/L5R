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
- [[Doji Junji]]
- [[Togashi Hanzo]]
- [[Kuni Yoshiyuki]]
- [[Doji Gaoxing]]
- [[Usagi Haku]]
- [[Akodo Yakisoba]]

## Overview

## Key Learnings

## Who Did We Meet?

## Items of Interest

## What Worked
