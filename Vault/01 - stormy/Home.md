---
banner: "![[Attachments/Purple_Sky.png]]"
banner_y: 0.4562
author: stormy
cssclasses:
  - hide-properties
  - dashboard
---
# 🏡Home

>[!multi-column]
> 
>> [!todo]+ Todo 
>> ```dataview 
>> TASK 
>> FROM "01 - stormy" 
>> WHERE contains(tags, "#Todo") AND !checked 
>> SORT file.ctime DESC
>> ```
> 
> >[!example]+ Tags
> >🔖 Tagged:  linux
> >`$=dv.list(dv.pages('#linux').sort(f=>f.file.name,"desc").limit(4).file.link)`
> 
> >[!summary]+ Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`


>[!multi-column] 
>
> >[!attention]+ Everyday
> > - [ ] eat
> > - [ ] sleep
> > - [ ] work
> > - [ ] repeat
>
> >[!Help]+ Stats
> > - File Count: `$=dv.pages().length`
> > - Projects: `$=dv.pages('"03 - Projects"').length`

