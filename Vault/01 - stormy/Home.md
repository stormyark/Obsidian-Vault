---
banner: "![[08 - Recources/Purple_Sky.png]]"
banner_y: 0.44857
author: stormy
cssclasses:
  - hide-properties
  - dashboard
---

```widgets
type: clock
format: "12hr" | "24hr"
```
>[!multi-column]
> 
>> [!todo]+ Todo 
>> ```dataview 
>> TASK 
>> FROM "01 - stormy" 
>> WHERE contains(tags, "#todo") AND !checked 
>> SORT file.ctime DESC
>> ```
> 
> >[!example]+ Tags
> >🔖 Tagged:  #code/javascript 
> >`$=dv.list(dv.pages('#code/javascript').sort(f=>f.file.name,"desc").limit(3).file.link)`
> 
> >[!summary]+ Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`

---
>[!multi-column] 
>
>>[!attention]+ Everyday
>> ```dataview 
>> TASK 
>> FROM "01 - stormy" 
>> WHERE contains(tags, "#today") AND !checked 
>> SORT file.ctime DESC
>> ```
>
> >[!Help]+ Stats
> > - File Count: `$=dv.pages().length`
> > - Projectfiles: `$=dv.pages('"03 - Projects"').length`
> > - #code tags: `$=dv.pages('#code').length`
---
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
// Create a visually appealing display that works in both light and dark modes
dv.paragraph(`<div style="
  background-color: transparent;
  border: 1px solid var(--background-modifier-border);
  border-radius: 6px;
  padding: 20px;
  text-align: center;
  font-family: var(--font-text);
  color: var(--text-normal);
">
  <h2 style="color: var(--text-normal);">📊 Obsidian Stats</h2>
  <p style="font-size: 16px; margin: 10px 0;">
    🗓️ You've been using Obsidian for <strong>${daysSinceStart}</strong> days
  </p>
  <p style="font-size: 16px; margin: 10px 0;">
    📝 You have <strong>${totalNotes}</strong> notes
  </p>
  <p style="font-size: 16px; margin: 10px 0;">
    🏷️ You're using <strong>${totalTags}</strong> unique tags
  </p>
</div>`)
```