---
banner: "![[Purple_Sky.png]]"
banner_y: 0.4562
cssclasses:
  - hide-properties
  - dashboard
---
# Home

>[!multi-column]
>
> >[!todo] Todo
> > - [ ] Todo 1
> > - [ ] Todo 2
> > - [ ] Todo 3
> 
> >[!example] Tags
> >🔖 Tagged:  linux
> >`$=dv.list(dv.pages('#linux').sort(f=>f.file.name,"desc").limit(4).file.link)`
> 
> >[!summary] Recent files
> >`$=dv.list(dv.pages('').sort(f=>f.file.mtime.ts,"desc").limit(4).file.link)`


>[!multi-column]
>
> >[!important] Stats
> > - File Count: `$=dv.pages().length`
> > - Projects: `$=dv.pages('"03 - Projects"').length`
> 
> >[!example]
> >lol
