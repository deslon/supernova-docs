
## Description

This class outputs logs platform independent.

### Methods

| Type          | Name                      |  Langs      |
| -----         | -----------               | ----------  |
| static void | [print](#print) | :material-language-cpp: \| :material-language-lua: |
| static void | [verbose](#verbose) | :material-language-cpp: \| :material-language-lua: |
| static void | [debug](#debug) | :material-language-cpp: \| :material-language-lua: |
| static void | [warn](#warn) | :material-language-cpp: \| :material-language-lua: |
| static void | [error](#error) | :material-language-cpp: \| :material-language-lua: |


## Methods details

### print

 * static void **print**(const char* text, ...)

:material-language-lua: Lua syntax:

 * void **print**(const char* text)

Print to output without label. In Android it assumes VERBOSE label.

 ---

### verbose

 * static void **verbose**(const char* text, ...)

:material-language-lua: Lua syntax:

 * void **verbose**(const char* text)

Print to output with VERBOSE label.

 ---

### debug

 * static void **debug**(const char* text, ...)

:material-language-lua: Lua syntax:

 * void **debug**(const char* text)

Print to output with DEBUG label.

 ---

### warn

 * static void **warn**(const char* text, ...)

:material-language-lua: Lua syntax:

 * void **warn**(const char* text)

Print to output with WARN label.

 ---

### error

 * static void **error**(const char* text, ...)

:material-language-lua: Lua syntax:

 * void **error**(const char* text)

Print to output with ERROR label.
