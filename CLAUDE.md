# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

GitHub profile README repo (brownjer3/brownjer3) featuring an animated dino runner display built with pure SVG + CSS animations. Retro terminal aesthetic (green on black) with code-symbol obstacles.

## Architecture

- `dino.svg` — Standalone SVG with embedded CSS `@keyframes` animations. Referenced via `<img>` tag in README so GitHub renders the animations.
- `README.md` — Profile page that displays the dino runner animation.

## Constraints

- No JavaScript (GitHub strips it from SVGs)
- No SMIL animations (`<animate>` / `<animateTransform>` — inconsistent GitHub support)
- No inline SVG in markdown (GitHub strips it)
- No external stylesheets or build tools
- SVG must use CSS `@keyframes` only for animation

## Key Pattern

All animations share an 8-second cycle. The dinosaur jumps twice per cycle, synchronized with two obstacle groups scrolling right-to-left. Ground texture marks scroll continuously for a sense of motion.
