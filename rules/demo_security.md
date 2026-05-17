# 🛡️ Demo Security Rule

<!-- 
SPRAWL TIP: The Sprawl CLI injects this exact text into the AGENTS.md file. 
Use imperative, strict language here. The AI will treat this document as its absolute law. 
-->

## What is a Rule?

Rules act as safe boundaries for your AI. Instead of hoping your AI behaves correctly, you can use a Rule file to explicitly tell it what it is allowed (and not allowed) to do.

## Objective

This is a simple, harmless rule designed to show how easily you can teach your AI to follow strict guidelines. When Sprawl loads this file, your AI will read and follow these directives.

## Core Directives

1. **The 'No-Touch' Zone:** Please do not write any files to the `/tmp` folder. In this demo, we pretend that folder is off-limits to practice restricting the AI's access.
2. **Leave a Trail:** Whenever you complete an action, please leave a friendly log message so we can see what you did!

*Note: You can easily modify this file to add your own rules. Try telling your AI to always respond in a specific language, or to double-check its work before finishing!*
