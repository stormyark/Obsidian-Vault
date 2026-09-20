---
author: stormy
cssclasses:
  - hide-properties
  - dashboard
  - no-embed-border
banner: "![[09 - Resources/sunrise.jpg]]"
banner_y: 0.33922
banner_x: 0.5
banner_lock: true
---

```widgets
type: clock
format: "12hr" | "24hr"
```
>[!multi-column]
>> [!summary]+ Tasks
>> ```dataview 
>> TASK 
>> FROM "01 - Private" 
>> WHERE contains(tags, "#todo") AND !checked 
>> SORT file.ctime DESC
>> ```
> 
> >[!example]+ Tags
> >🔖 Tagged:  #code/javascript 
> >`$=dv.list(dv.pages('#code/javascript').sort(f=>f.file.name,"desc").limit(3).file.link)`
> 
> >[!error]+ Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`

> [!done]+ Todo 
> ![[01 - Private/Projects.base|Projects]]

```dataviewjs
// Calculate days since first note
const files = dv.pages()
const oldestFile = files.sort(f => f.file.ctime)[0]
const daysSinceStart = Math.floor((Date.now() - oldestFile.file.ctime) / (1000 * 60 * 60 * 24))
// Count total notes
const totalNotes = files.length
// Count unique tags
const allTags = files.flatMap(p => p.file.tags).distinct()
const totalTags = allTags.length
//const totalFolders = folders.length
// Create a visually appealing display that works in both light and dark modes
dv.paragraph(`<div style="
  background-color: transparent;
  border: 1px solid var(--background-modifier-border);
  border-radius: 0.5em;
  padding: 20px;
  text-align: center !important;
  font-family: var(--font-text);
  color: var(--text-normal);
">
  <h2 style="font-size: 28px; color: var(--text-normal); text-align: center !important;">📊 Obsidian Stats</h2>
  <p style="font-size: 16px; margin: 10px 0; text-align: center !important;">
    🗓️ You've been using Obsidian for <strong>${daysSinceStart}</strong> days
  </p>
  <p style="font-size: 16px; margin: 10px 0; text-align: center !important;">
    🏷️ You're using <strong>${totalTags}</strong> unique tags
  </p>
  <p style="font-size: 16px; margin: 10px 0; text-align: center !important;">
    📝 You have <strong>${totalNotes}</strong> notes
  </p>
</div>`)
```


```contributionGraph
graphType: default
dateRangeValue: 365
dateRangeType: LATEST_DAYS
startOfWeek: "1"
showCellRuleIndicators: true
titleStyle:
  textAlign: center
  fontSize: 40px
  fontWeight: normal
dataSource:
  type: PAGE
  value: ""
  dateField:
    type: FILE_MTIME
  countField:
    type: DEFAULT
fillTheScreen: true
enableMainContainerShadow: false
cellStyleRules:
  - id: mauve_1
    min: 1
    max: 2
    color: "#CBA6F7"
  - id: mauve_2
    min: 2
    max: 3
    color: "#AF77F3"
  - id: mauve_3
    min: 3
    max: 5
    color: "#9348EF"
  - id: mauve_4
    min: 5
    max: 999
    color: "#7719EA"
cellStyle:
  minHeight: 16px
  minWidth: 4px

```
