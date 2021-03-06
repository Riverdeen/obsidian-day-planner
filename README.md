# Day Planner

![GitHub Workflow Status](https://img.shields.io/github/workflow/status/lynchjames/obsidian-day-planner/Release%20Build?logo=github&style=for-the-badge) ![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/lynchjames/obsidian-day-planner?style=for-the-badge&sort=semver)


This repository contains a plugin for [Obsidian](https://obsidian.md/) for day planning and managing pomodoro timers from a task list in a Markdown note. 

> This is an early alpha of version of the plugin and it will be running constantly in the background while Obsidian is open and the plugin is enabled. **Please try the plugin in a test vault first, and, most importantly, make sure you have your notes backed up in cloud storage or Git.**
    
## Usage
Once installed, the plugin will create a folder called Day Planners in the root of your vault. A note for today will automatically be created with the file name format `Day Planners/Day Planner-YYYYMMDD.md`.

You can choose to use the [Command Mode](#day-planner-mode) instead to add a Day Planner for the current day to any note.

### Day Planner Note

Within the note, you can create a check list with times and tasks which will be automatically be tracked during the day. Here is an example:

```markdown
## Day Planner
- [ ] 09:30 Setup for work
- [ ] 09:45 Review notes from yesterday
- [ ] 10:30 Create new notes for #article review
- [ ] 11:30 BREAK
- [ ] 12:00 Reading
- [ ] 12:25 BREAK
- [ ] 12:30 Reading
- [ ] 14:00 BREAK
- [ ] 15:00 Review notes and update daily note [[20201103]]
- [ ] 15:45 Walk
- [ ] 16:30 Reading
- [ ] 17:20 Prep for tomorrow's meetings
- [ ] 18:00 END

---
```

This is also provided as a file in [day-planner-example.md](https://github.com/lynchjames/obsidian-day-planner/blob/main/examples/day-planner-example.md).

The Day Planner heading and `---` rule are used to identify the extent of the Day Planner. A heading must be used but can be `#`, `##`, `###` or `####`.

The format of the task list items is important as this is what is used to calculate the times of each task and the intervals between tasks. The format used should be:

 `- [ ] HH:mm Task text` 
 
 **24 hour times should be used.** 

 `BREAK` and `END` are keywords that define breaks and the end to the time tracking for the tasks. They are not case sensitive so `break` and `end` can also be used.

 `END` is used as an item with a time to give an accurate time interval for the last task, *"Prep for tomorrow's meetings"* at 17:00 in this example.

 The note will update automatically in the following ways:

 - Tasks in the past will be checked and marked as complete.
 - The current task will be called out and a progress indicator will be included in the note.

Using the example above, at 14:30 the note would have automatically updated to:

```markdown
## Day Planner
- [x] 09:30 Setup for work
- [x] 09:45 Review notes from yesterday
- [x] 10:30 Create new notes for #article review
- [x] 11:30 BREAK
- [x] 12:00 Reading
- [x] 12:25 BREAK
- [x] 12:30 Reading

**Current Task**
- [ ] 14:00 BREAK

> ||14:00||->->->->->->->->->->_ _ _ _ _ _ _ _ ||15:00||

- [ ] 15:00 Review notes and update daily note [[20201103]]
- [ ] 15:45 Walk
- [ ] 16:30 Reading
- [ ] 17:20 Prep for tomorrow's meetings
- [ ] 18:00 END

---
```

This would also be displayed in preview mode:

![Day Planner Note Preview](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/day-planner-note-preview.png)

### Status Bar

The status bar in Obsidian will also show the current progress on the task or break with the time remaining. Clicking on the status bar item will take you to the Day Planner note.

#### Task Status

The status displayed when there is an active task:

![Task Status](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/task-status.png)

#### Break Status

The status displayed during a break:

![Break Status](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/break-status.png)

#### End Status

The status displayed when the end of the tasks is reached:

![End Status](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/end-status.png)

## Configuration

### Day Planner Mode

There are 2 modes to use the Day Planner plugin:

**File mode**

The plugin automatically generates day planner notes for each day within a Day Planners folder.

**Command mode**

Commands are used to insert a Day Planner for today within any note as well as unlinking the Day Planner for today from its current note.

The Day Planner can be placed anywhere within a note as long as the format provided is used. Only the Day Planner section of the note will be updated as time progresses.

### Complete Past Planner Items

You can choose whether the plugin will automatically mark planner items in the past as complete or allow you to tick them off yourself.

### Mermaid Gantt

You can choose to include a dynamically generated [Mermaid Gantt chart](https://mermaid-js.github.io/mermaid/#/gantt) in your Day Planner.

Tasks and breaks will be displayed in separate sections to help visualise your plan for the day.

![Mermaid Gantt Chart Example](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/mermaid-gantt.png)

Colors for the gantt chart can be overridden with custom CSS and there is [Mermaid documentation](https://mermaid-js.github.io/mermaid/#/gantt?id=styling) on the classes. A CSS file with examples for the task and breaks sections is provided:

[mermaid-gantt-example.css](examples/mermaid-gantt-example.css)

## Commands

Using the plugin in command mode, 2 commands are available to link and unlink a Day Planner.

![Plugin Commands](https://raw.githubusercontent.com/lynchjames/obsidian-day-planner/main/images/commands.png)

## Compatibility

Custom plugins are only available for Obsidian v0.9.7+.

The current API of this repo targets Obsidian **v0.9.10**. 

## Installing

As of version [0.9.7 of Obsidian](https://forum.obsidian.md/t/obsidian-release-v0-9-7-insider-build/7628), this plugin is available to be installed directly from within the app. The plugin can be found in the Community Plugins directory which can be accessed from the Settings pane under Third Party Plugins.

## Manual installation

1. Download the [latest release](https://github.com/lynchjames/obsidian-day-planner/releases/latest)
1. Extract the obsidian-day-planner folder from the zip to your vault's plugins folder: `<vault>/.obsidian/plugins/`  
Note: On some machines the `.obsidian` folder may be hidden. On MacOS you should be able to press `Command+Shift+Dot` to show the folder in Finder.
1. Reload Obsidian
1. If prompted about Safe Mode, you can disable safe mode and enable the plugin.

## For developers
Pull requests are both weclcome and appreciated. 😀

If you would like to contribute to the development of this plugin, please follow the guidelines provided in [CONTRIBUTING.md](CONTRIBUTING.md).

## Donating

This plugin is provided free of charge. If you would like to donate something to me, you can via [PayPal](https://paypal.me/lynchjames2020). Thank you!
