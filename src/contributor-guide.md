# Contributor Guide

### How to commit

List of good resources to find out what to do:
  - [Good first Issues](https://github.com/pyanodon/pybugreports/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22good%20first%20issue%22)
  - [Py Roadmap](https://github.com/orgs/pyanodon/projects/2/views/4)

How can I contribute?
  1. Clone the repo you want to commit to
  2. Create a new branch off of main
  3. Create the changes you want to add
  4. Create a pull request describing what you fixed or what you're adding, for simple bug reports you can just say “Fixes <issue link>”
  5. Wait for approval
  6. Make changes if needed
  7. Boom dopamine

### General Layout

We have 2 branches for different updates: Master or Main and Breaking Changes
- Main or Master is used for bug fixes, general fixes, or non-removing enhancements.
- Breaking changes is used for breaking changes like changing the output of a recipe to have a new byproduct.

The codebase will look something like this typically
```
pytesting
├── control.lua
├── data.lua
├── scripts
│      └── example.lua
└── prototypes
         ├── buildings
         │      └── example-building.lua
         ├── items
         │      └── items.lua
         ├── recipes
         │      └── recipes.lua
         └── technologies
                  └── exmple-technology.lua
```

### Frequently Asked Questions

Where are pypostprocessing functions located at?

`pypostprocessing/lib` for in-general stuff<br>
`pypostprocessing/lib/metas` for prototyping functions<br>
`pypostprocessing/lib/events` for control event functions
