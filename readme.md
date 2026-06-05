# LuaTools Steam Plugin (Fork)

Based on [LuaTools Steam Plugin](https://github.com/piqseu/ltsteamplugin) by piqseu.

## Implemented Fixes in this Fork:
1. **Unpacked Named Arguments for Millennium API Calls**:
   - Modern versions of Millennium pass JS objects as a single table (dictionary) in `callServerMethod`. 
   - Updated `StartAddViaLuaToolsFromUrl` and `ApplyGameFix` in `backend/main.lua` to check if arguments are received as a table and unpack them, ensuring compatibility with both old (positional) and new (table-based) parameter styles.
2. **Fixed Background Process Escaping on Windows**:
   - Fixed quoting issue when spawning background downloader/fix processes via `m_utils.exec` (CMD).
   - Replaced escaped nested double quotes (`\"`) with doubled single quotes (`''`) inside the PowerShell `-ArgumentList` parameter. This prevents CMD from stripping quotes and ensures paths containing spaces (like `C:\Program Files (x86)\...`) are handled correctly without crashing.
3. **Corrected Morrenus API Availability Check**:
   - The Morrenus status API returns `HTTP 200 OK` even if the app is not in their library (returning `"status": "not_found"` in the JSON body).
   - Updated the availability checks in `downloads.start_add_via_luatools` and `downloads.check_apis_for_app` to decode the JSON body and verify that status is not `"not_found"` before flagging it as available.

## Before submitting PRs, keep in mind:
The plugin will go through a full rewrite in the near future, so if you want to contribute, wait until the rewrite is open sourced.
Issues will still be open and fixed on a case by case basis.
https://discord.gg/luatools
