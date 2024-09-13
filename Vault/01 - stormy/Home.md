---
banner: "![[Purple_Sky.png]]"
banner_y: 0.5
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
> >🔖 Tagged:  #linux
> >`$=dv.list(dv.pages('#linux').sort(f=>f.file.name,"desc").limit(3).file.link)`
> 
> >[!summary]+ Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`


>[!multi-column] 
>
> >[!attention]+ Everyday
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

