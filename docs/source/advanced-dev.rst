Advanced Development using DVN
======

This document describes advanced features of DVN and how to use them.

This document is a WIP and each entry is a placeholder.

Frame Loop & Loop Overrides
==============

how the frame loop is structured

how to inject logic before/after render

how to modify rendering per-window

recommended use cases

performance considerations

Multi-Window / Multi-Instance Support
==============

how to create extra windows

how rendering differs between them

how to sync states between windows

use cases (debug tools, second viewpoints, HUD windows)

Custom Rendering Pipelines (OpenGL, 2D/3D, Overlays)
==============

drawing your own objects

hooking OpenGL directly

layering effects

injecting shaders

replacing DVN's renderer

Networking (Multiplayer / Streaming)
==============

high-level approach

recommended architecture

how VNs sync story states

streaming assets

multiplayer story use cases

Script Data Injection (injectGameScript)
==============

how it works

how to transform script keys

use cases

modding support

auto-translation hooks

AI-generated content injection

dynamic branching

analytics tags

safety considerations

Modifying or Replacing Built-in UI Components
==============

dialogue boxes

character name plates

option buttons

history/log display

main menu

settings menu

save/load menus

Full Engine Theming & Reskinning
==============

global styles

how to override all panels/buttons

dynamic theme switching

using external data for styles

Dynamic Character Models (States, Directions, Actions)
==============

how to hook character states

how to tie states to events

how to animate procedurally

using character models in custom views

DOM / CSS3 / Markdown Parsing
==============

parsing HTML/XML/SVG for content

using CSS selectors to find content

loading dialogue or scenes from Markdown

using theming via CSS-like selectors

Custom Save/Load Logic
==============

intercepting save

encrypting save data

save file metadata

cloud sync

custom thumbnails

Extended Debugging / Diagnostics (Advanced)
==============

using overlays

rendering debug info

leveraging frame-loop events for debug

performance analysis

script loading logs

multi-window debugging

Internal Engine Architecture Overview
==============

view stack

script loader lifecycle

rendering lifecycle

asset pipeline

save/load lifecycle
