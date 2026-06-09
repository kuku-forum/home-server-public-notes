# Dashboards

The Home Assistant UI is split by use case instead of trying to show every
device everywhere.

## Phone Dashboard

The phone dashboard is the daily control surface. It prioritizes:

- fast room and scene control
- common climate controls
- bathroom and ventilation state
- key system health cues
- device groups that are easy to scan on a small screen

Risky maintenance controls are grouped separately from everyday controls.

## Wallpad Dashboard

The wallpad dashboard is for a mounted tablet in landscape orientation. It is a
command board, not a stretched phone UI.

It prioritizes:

- high information density
- direct control of lights, climate, curtains, bathroom state, and media
- readable status at a glance
- stable rendering in mobile and tablet WebViews

## E-paper Preparation

An e-paper dashboard concept was prepared for a small display. The important
design decision was to separate setup controls from the final render area. Only
the content image intended for the e-paper display should be treated as the
device output.

## UI Lessons

- Keep daily dashboards small and purposeful.
- Keep admin and maintenance actions away from casual control areas.
- Treat experimental dashboards as separate surfaces.
- Verify custom dashboard code in the actual target WebView.
- Avoid relying on fragile text encoding in custom card source files.

## Not Included

This repo does not publish dashboard paths, resource files, screenshots of the
private home, full Lovelace exports, or custom card source code.
