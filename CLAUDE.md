# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static HTML website that tracks MLB no-hitters and perfect games. The site displays baseball games for a selected date, highlighting games where teams are currently throwing no-hitters or perfect games. The website is hosted at www.no-no.games.

## Development Setup

This is a pure HTML/CSS/JavaScript project with no build process or dependencies. To develop:

1. Open `index.html` directly in a browser
2. Make changes to the single HTML file containing all code
3. Refresh browser to see changes

## Architecture

The entire application is contained in a single `index.html` file with:

- **Embedded CSS**: All styling is in a `<style>` block in the document head
- **Embedded JavaScript**: All functionality is in a `<script>` block before the closing body tag
- **Template-based rendering**: Uses HTML `<template>` elements for game and date display
- **MLB API integration**: Fetches live game data from `statsapi.mlb.com`

### Core Classes

- `Game`: Represents a baseball game with methods to determine no-hitter/perfect game status
- `Team`: Represents a baseball team with tracking for when they lose no-hitter/perfect status

### Key Functions

- `main()`: Entry point that sets up URL handling and loads initial date
- `load(date)`: Fetches game data for a specific date and updates the display
- `layout_games()`: Renders game cards, sorted by importance (perfect games first, then no-hitters, then live games)
- `layout_dates()`: Renders the date navigation bar

### Data Flow

1. Parse URL date parameter or use current date
2. Fetch MLB schedule for that date
3. For each game, fetch detailed live data
4. Analyze play-by-play data to determine no-hitter/perfect game status
5. Sort and display games with appropriate highlighting

### Game Status Logic

- **Perfect Game**: No baserunners allowed (tracks when first runner reaches base)
- **No-Hitter**: No hits allowed (tracks inning when first hit occurs)
- Games are highlighted with green backgrounds when active no-hitters/perfect games are occurring

## File Structure

- `index.html`: Complete application
- `img/`: Favicon files
- `CNAME`: GitHub Pages domain configuration
- `*.json/*.tsv`: Example data downloaded from the MLB API

## URL Structure

The site supports date navigation via URL parameters:
- `?date=YYYY-MM-DD` to view games for a specific date
- Uses browser history API for navigation

## Code Quality Guidelines

- Keep the code clean and understandable. 
- Keep functions single purpose and well named. 
- Only use comments where it helps to clarify something that might be confusing.