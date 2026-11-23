# to-do

A to-do list app with projects, priorities, due dates and editable notes, built for [The Odin Project](https://www.theodinproject.com/) curriculum.

**Live demo:** https://equanimity-studio.github.io/to-do/

Built with HTML, CSS and vanilla JavaScript, bundled with webpack.

## Features

- Create to-dos with a title, details, due date and priority level
- Check off or delete to-dos, and edit them after creating them
- Group to-dos into projects; the Home page shows every to-do across all projects
- Write and edit notes, newest first, in horizontally scrolling columns
- Data is saved in the browser with `localStorage`
- Three layouts for different screen sizes

## What I learned

- **Splitting code into ES modules** with `import`/`export`, and bundling them with webpack (CSS, font and image loaders, plus a script that deploys to GitHub Pages)
- **Using classes** (`TD`, `Proj`, `Note`) to give each kind of data a consistent shape
- **Saving and restoring app state** with `localStorage` and `JSON.stringify`/`JSON.parse`, including loading sample content the first time the app opens
- **Building the whole interface from JavaScript**: creating, cloning and removing DOM elements as data changes
- **Responsive design** with CSS Grid and media queries

## Looking back: what I'd do differently

This was my biggest project at the time, and rereading it showed me what I need to work on:

- **Keep one source of truth.** The app often reads its state back from the page (button text, CSS classes) instead of from the data. I'd keep the data in one place and re-draw the page from it.
- **Stop repeating code.** The "hide every panel, show one, highlight the active button" logic is copied about eight times. It should be one function.
- **Use clearer names.** Abbreviations like `TD`, `projs`, `det` and `prio` were quick to type but are hard to read later. I now spell names out (`Todo`, `projects`, `detailsButton`) and use one name per idea, not `name` in one place and `title` in another.
- **Use real booleans.** Checked state is stored as the strings `"checked"`/`"unchecked"`; `isChecked: true/false` is simpler and safer.
- **Find things by ID, not by name.** Each to-do has an `id`, but deleting matches by name, so two to-dos with the same name get deleted together.

**Known bug:** a to-do's checkmark doesn't stay checked after a page refresh. A comparison was written as `=` instead of `===`, so the change is never saved.
