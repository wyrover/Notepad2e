=======================================================================
=                                                                     =
=                                                                     =
=  Notepad 2e - light-weight Scintilla-based text editor for Windows  =
=                                                                     =
=                                                                     =
=                                                    Notepad2 4.2.25  =
=                                       (c) Florian Balmer 2004-2011  =
=                                        http://www.flos-freeware.ch  =
=                                                                     =
=  Extended edition (c) 2013-2014                                     =
=                                                                     =
=                                            by Proger_XP and haccel  =
=                              https://github.com/ProgerXP/Notepad2e  =
=                                                                     =
=======================================================================


The Notepad2 Source Code

  This package contains the full source code of Notepad2 4.2.25 for
  Windows. Project files for Visual C++ 7.0 are included. Chances are
  that Notepad2 can be rebuilt with other development tools, including
  the free Visual C++ Express Edition, but I haven't tested this.


Rebuilding from the Source Code

  Notepad2 4.2.25 is based on Scintilla 2.24 [1].

  [1] http://www.scintilla.org

  To be able to rebuild Notepad2, the source code of the Scintilla
  editing component has to be unzipped to the "scintilla" subdirectory
  of the Notepad2 source code directory.

  Many of the Scintilla lexing modules are not used by Notepad2. Run
  LinkLex.js to adapt the list (in "scintilla/src/Catalogue.cxx") and
  make linking work properly.


Creating a Compact Executable Program File

  Linking to the system CRT slightly improves disk footprint, memory
  usage and startup because the pages for the system CRT are already
  loaded and shared in memory. To achieve this, the release version of
  Notepad2.exe is built using the Windows Driver Kit (WDK) 7.1.0 tools,
  available as a free download from Microsoft. The appropriate build
  scripts can be found in the "wdkbuild" subdirectory. Set %WDKBASEDIR%
  to the directory of the WDK tools on your system.


How to add or modify Syntax Schemes

  The Scintilla documentation has an overview of syntax highlighting,
  and how to write your own lexing module, in case the language you
  would like to add is not currently supported by Scintilla.

  Add your own lexer data structs to the global pLexArray (Styles.c),
  then adjust NUMLEXERS (Styles.h) to the new total number of syntax
  schemes. Include the "scintilla/lexers/Lex*.cxx" file required for
  your language into your project. Ensure the new module is initialized
  (in "scintilla/src/Catalogue.cxx"), either by manually uncommenting
  the corresponding LINK_LEXER() macro call, or by updating and
  re-running LinkLex.js.


Copyright

  See License.txt for details about distribution and modification.

  If you have any comments or questions, please drop me a note:
  florian.balmer@gmail.com

  (c) Florian Balmer 2004-2011
  http://www.flos-freeware.ch

  (c) Proger_XP and co.
  http://proger.me


Changes of the Extended edition

  Current Word Highlighting - with customizable formatting (rectangle,
  border, etc.) and colors. 3 modes: one occurrence in document, two
  or more but all are visible, multiple with some hidden under scroll.

  Go to Last Change (Ctrl+Shift+Z) - moves caret to the position of last
  Undo action.

  Retain caret position and selection when file is re-coded (File >
  Encoding items).

  Case-insensitive Find for Cyrillic characters - previously search was
  always case-sensitive regardless of Match case flag.

  Trimming Go to - now in Line and Column first number substring is
  extracted and used to navigate. For example, "abc567.89" will navigate
  to 567.

  Go to Absolute Offset - extension of Goto (Ctrl+G) dialog. Respects
  different charsets.

  Replace Settings in All Instances - very useful if you have dozens of
  Notepad2 windows open and need to change settings in one of them;
  select this to make all others reload them from disk (not from this
  instance).

  Reload Settings from Disk (Alt+F7) - replace all settings in current
  window with fresh version read from Notepad2.ini.

  Open Previous (Alt+G) - lets you toggle between two most recent
  History files with one keystroke.

  Remember Insert Tag - now Opening and Closing tags are retained until
  Notepad is closed.

  File Shell Menu (Alt+R) - invokes Explorer's context menu for
  currently opened file.

  Rename To (Alt+F6) - acts as Save As but deletes original file on
  success.

  File > Encoding > UTF-8 now has Shift+F8 hotkey assigned.

  Open Dialog allows opening by prefix - so instead of typing the full
  file name or selecting with your mouse you can only type name's
  beginning and hit Enter or click Open to open the first matching file.
  This is disabled by default.

  Better Save To Dialog - new file extension is determined first by
  DefaultExtension INI setting (as before) but then if current file was
  previously opened from or saved to disk its old extension is used as
  default (even if it's empty). If new file name ends on period file is
  saved without extension.

  Ctrl+Wheel Scroll - very handy to navigate long scripts. Roll the
  wheel while holding Ctrl down to scroll through entire pages (similar
  to Page Up/Down).

  Open/Save File dialogs now start with the path of last opened file.
  
  Edit > Copy Add (Ctrl+E) now uses single line break and when pressed
  without active selection appends the entire line.
  
  File > Launch > Command (Ctrl+R) now retains the path until another
  file is opened.
  
  Find (Ctrl+F) now has Grep/Ungrep buttons (working on regexp too).
  
  Insert HTML Tag (Alt+X) now skips whitespace within the selection.

  CSS syntax scheme improvements:

    - Added CSS 3 properties.

    - Enabled //-inline comments (Ctrl+Q) that are used in LESS, SASS
      and other preprocessors.

    - Fixed brackets of nested rules that were not matching in some
      cases (visually and with Ctrl+B).


###
