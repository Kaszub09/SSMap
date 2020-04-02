# Salt &amp; Sanctuary Interactive Map
Map was created using screenshot map by **u/magicofgames** from reddit: https://www.reddit.com/r/saltandsanctuary/comments/f0t1sa/ultimate_map_still_wip_well_no_but_actually_yes/



## Edit
Currently, all the info about markers is read from markers.js. If you would like to add some new marker:
1. Download repo.
2. Uncomment Save ans Add new marker buttons and set markers draggable to true in index.html. (Optionally change to read markers from localStorage insteaf of file)
3. Now you can edit markers. All changes are save in localStorage.
4. Acces localStorage, copy AllMarkers value, format it into JSON (e.g. using notepad++ plugin), replace '\' with '\\' and copy/paste new markers at the end of markers.js

## Things that would be nice to have:
- Storing markers info in database
- Login, Registration
- Mark as completed implementation
