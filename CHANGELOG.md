## Release Notes

### 2.0.2
  - Adds auto-enable of whitespace toggling when using font-ligatures because of [vscode issue](https://github.com/Microsoft/vscode/issues/11485)
  - Adds `gitlens.blame.annotation.characters.*` settings to provide some control over how annotations are displayed
  - Fixes [#22](https://github.com/eamodio/vscode-gitlens/issues/22) - Cannot read property 'sha' of undefined

### 2.0.1
  - Fixes [#26](https://github.com/eamodio/vscode-gitlens/issues/26) - Active line annotation doesn't disappear properly after delete

### 2.0.0
  - Adds `gitlens.blame.annotation.activeLine` to specify whether and how to show blame annotations on the active line
  - Adds full commit message (rather than just summary) to active line hover if `gitlens.blame.annotation.activeLine` is not `off`
  - Adds new `trailing` blame annotation style -- adds annotations after the code lines rather than before
  - Adds `gitlens.blame.annotation.message` to show the commit message in `expanded` and `trailing` blame annotaion styles
  - Adds support for relative dates in blame annotations. Use `gitlens.blame.annotation.date`
  - Changes the design of hover annotations -- much cleaner now
  - Disables automatic whitespace toggling by default as it is seemingly no longer needed as [vscode issue](https://github.com/Microsoft/vscode/issues/11485) seems fixed. It can be re-enabled with `gitlens.advanced.toggleWhitespace.enabled`
  - Fixes issue where the statusBar blame would get stuck switching between editors
  - Fixes issue where CodeLens aren't updated properly after a file is saved
  - Re-adds context menu for `gitlens.diffLineWithPrevious` -- since [vscode issue](https://github.com/Microsoft/vscode/issues/15395)
  - Re-adds context menu for `gitlens.diffLineWithWorking` -- since [vscode issue](https://github.com/Microsoft/vscode/issues/15395)

### 1.4.3
  - Adds some logging to hopefully trap [#22](https://github.com/eamodio/vscode-gitlens/issues/22) - Cannot read property 'sha' of undefined
  - Fixes issue with the latest insiders build (1.9.0-insider f67f87c5498d9361c0b29781c341fd032815314b) where there is a collision of document schemes

### 1.4.2
  - Fixes issue where file history wouldn't compare correctly to working tree if the filename had changed

### 1.4.1
  - Adds `gitlens.advanced.gitignore.enabled` to enable/disable .gitignore parsing. Addresses [#20](https://github.com/eamodio/vscode-gitlens/issues/20) - Nested .gitignore files can cause blame to fail with a repo within another repo

### 1.4.0

  - Adds `alt+h` shortcut for the `gitlens.showQuickFileHistory` command
  - Adds `shift+alt+h` shortcut for the `gitlens.showQuickRepoHistory` command
  - Adds `gitlens.advanced.maxQuickHistory` to limit the number of quick history entries to show (for better performance); Defaults to 200
  - Adds `gitlens.diffLineWithPrevious` as `alt` context menu item for `gitlens.diffWithPrevious`
  - Adds `gitlens.diffLineWithWorking` as `alt` context menu item for `gitlens.diffWithWorking`
  - Adds `gitlens.showFileHistory` as `alt` context menu item for `gitlens.showQuickFileHistory`
  - Removes context menu for `gitlens.diffLineWithPrevious` -- since it is now the `alt` of `gitlens.diffWithPrevious`
  - Removes context menu for `gitlens.diffLineWithWorking` -- since it is now the `alt` of `gitlens.diffWithWorking`
  - Replaces `gitlens.menus.fileDiff.enabled` and `gitlens.menus.lineDiff.enabled` with `gitlens.menus.diff.enabled` -- since the switch between file and line diff is now controlled by the `alt` key

### 1.3.1

  - Renames `Diff` commands for better clarity
  - Removes `Git` from the commands as it feels unnecessary
  - Reorders the context menu commands
  - Adds `Diff Commit with Working Tree` to the explorer context menu (assuming `gitlens.menus.fileDiff.enabled` is `true`)
  - Adds `Diff Commit with Working Tree` & `Diff Commit with Previous` to the editor title context menu (assuming `gitlens.menus.fileDiff.enabled` is `true`)

### 1.3.0

  - Adds support for blame and history (log) on files opened via compare commands -- allows for deep navigation through git history

### 1.2.0

  - Adds compare (working vs previous) options to repository history
  - Adds compare (working vs previous) options to file history
  - Fixes issue with repository history compare with commits with multiple files

### 1.1.1

  - Allows `gitlens.showQuickRepoHistory` command to run without an open editor (falls back to the folder repository)
  - Adds logging for tracking [#18](https://github.com/eamodio/vscode-gitlens/issues/18) - GitLens only displayed for some files

### 1.1.0

  - Adds new `gitlens.showQuickFileHistory` command to show the file history in a quick-pick list (palette)
  - Adds new `gitlens.showQuickRepoHistory` command to show the repository history in a quick-pick list (palette)
  - Adds `gitlens.showQuickFileHistory` option to the `gitlens.codeLens.recentChange.command`, `gitlens.codeLens.authors.command`, and `gitlens.statusBar.command` settings
  - Removes `git.viewFileHistory` option from the `gitlens.codeLens.recentChange.command`, `gitlens.codeLens.authors.command`, and `gitlens.statusBar.command` settings
  - Changes the `gitlens.statusBar.command` settings default to `gitlens.showQuickFileHistory` instead of `gitlens.toggleBlame`

### 1.0.2

  - Fixes [#16](https://github.com/eamodio/vscode-gitlens/issues/16) - incorrect 'Unable to find Git' message

### 1.0.0

  - Adds support for git history (log)!
  - Adds support for blame annotations and git commands on file revisions
  - Adds ability to show multiple blame annotation at the same time (one per vscode editor)
  - Adds new `gitlens.showFileHistory` command to open the history explorer
  - Adds new `gitlens.showFileHistory` option to the `gitlens.codeLens.recentChange.command`, `gitlens.codeLens.authors.command`, and `gitlens.statusBar.command` settings
  - Adds per-language CodeLens location customization using the `gitlens.codeLens.languageLocations` setting
  - Adds new `gitlens.diffLineWithPrevious` command for line sensitive diffs
  - Adds new `gitlens.diffLineWithWorking` command for line sensitive diffs
  - Adds `gitlens.diffWithPrevious` command to the explorer context menu
  - Adds output channel logging, controlled by the `gitlens.advanced.output.level` setting
  - Switches on-demand CodeLens to be a global toggle (rather than per file)
  - Complete rewrite of the blame annotation provider to reduce overhead and provide better performance
  - Improves performance of the CodeLens support
  - Improves performance (significantly) when only showing CodeLens at the document level
  - Improves performance of status bar blame support
  - Changes `gitlens.diffWithPrevious` command to always be file sensitive diffs
  - Changes `gitlens.diffWithWorking` command to always be file sensitive diffs
  - Removes all debug logging, unless the `gitlens.advanced.debug` settings it on
  - Fixes many (most?) issues with whitespace toggling (required because of https://github.com/Microsoft/vscode/issues/11485)
  - Fixes issue where blame annotations would not be cleared properly when switching between open files

### 0.5.5

  - Fixes another off-by-one issue when diffing with caching

### 0.5.4

 - Fixes off-by-one issues with blame annotations without caching and when diffing with a previous version

### 0.5.3

 - Adds better uncommitted hover message in blame annotations
 - Adds more protection for dealing with uncommitted lines

### 0.5.2

 - Fixes loading issue on Linux

### 0.5.1

 - Adds blame information in the StatusBar
 - Add new StatusBar settings -- see **Extension Settings** above for details
 - Renames the `gitlens.codeLens.recentChange.command` & `gitlens.codeLens.authors.command` settings options (to align with command names)
 - Adds new `gitlens.diffWithPrevious` option to the `gitlens.codeLens.recentChange.command` & `gitlens.codeLens.authors.command` settings
 - Fixes Diff with Previous when the selection is uncommitted
 - Removes `gitlens.blame.annotation.useCodeActions` setting and behavior

### 0.3.3

  - Fixes [#7](https://github.com/eamodio/vscode-gitlens/issues/7) - missing spawn-rx dependency (argh!)

### 0.3.2

  - Fixes [#7](https://github.com/eamodio/vscode-gitlens/issues/7) - missing lodash dependency

### 0.3.1

 - Adds new CodeLens visibility & location settings -- see **Extension Settings** above for details
 - Adds new command to toggle CodeLens on and off when `gitlens.codeLens.visibility` is set to `ondemand`

### 0.2.0

 - Fixes [#1](https://github.com/eamodio/vscode-gitlens/issues/1) - Support blame on files outside the workspace repository
 - Replaces blame regex parsing with a more robust parser
 - Fixes failures with Diff with Previous command
 - Fixes issues with blame explorer CodeLens when dealing with previous commits
 - Fixes display issues with compact blame annotations (now skips blank lines)

### 0.1.3

 - Improved blame annotations, now with sha and author by default
 - Add new blame annotation styles -- compact and expanded (default)
 - Adds many new configuration settings; see **Extension Settings** above for details

### 0.0.7

 - Fixes [#4](https://github.com/eamodio/vscode-gitlens/issues/4) - Absolute paths fail on Windows due to backslash (Really!)
 - Fixes [#5](https://github.com/eamodio/vscode-gitlens/issues/5) - Finding first non-white-space fails sometimes
 - Adds .gitignore checks to reduce the number of blame calls

### 0.0.6

 - Fixes [#2](https://github.com/eamodio/vscode-gitlens/issues/2) - [request] Provide some debug info when things fail
 - Fixes [#4](https://github.com/eamodio/vscode-gitlens/issues/4) - Absolute paths fail on Windows due to backslash
 - Attempts to scroll to the correct position when opening a diff

### 0.0.5

- Fixes issues where filename changes in history would cause diffs to fails
- Fixes some issues with uncommitted blames
- Removes CodeLens from fields and single-line properties to reduce visual noise
- Automatically turns off blame only when required now

### 0.0.4

Candidate for preview release on the vscode marketplace.

### 0.0.1

Initial release but still heavily a work in progress.