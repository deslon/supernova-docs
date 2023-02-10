
## Description

This class has input state information and all keys and modifiers codes to help input handle.

### Methods

| Type          | Name                      |  Langs      |
| -----         | -----------               | ----------  |
| static bool | [isKeyPressed](#iskeypressed) | :material-language-cpp: \| :material-language-lua: |
| static bool | [isMousePressed](#ismousepressed) | :material-language-cpp: \| :material-language-lua: |
| static bool | [isTouch](#istouch) | :material-language-cpp: \| :material-language-lua: |
| static bool | [isMouseEntered](#ismouseentered) | :material-language-cpp: \| :material-language-lua: |
| static Vector2 | [getMousePosition](#getmouseposition) | :material-language-cpp: \| :material-language-lua: |
| static Vector2 | [getMouseScroll](#getmousescroll) | :material-language-cpp: \| :material-language-lua: |
| static Vector2 | [getTouchPosition](#gettouchposition) | :material-language-cpp: \| :material-language-lua: |
| static std::vector<Touch\> | [getTouches](#gettouches) | :material-language-cpp: \| :material-language-lua: |
| static size_t | [numTouches](#numtouches) | :material-language-cpp: \| :material-language-lua: |
| static int | [getModifiers](#getmodifiers) | :material-language-cpp: \| :material-language-lua: |
| static size_t | [findTouchIndex](#findtouchindex) | :material-language-cpp: \| :material-language-lua: |


##  Structs

### Touch

Has info of touch event.

* int **pointer** - Pointer information for multitouch
* Vector2 **position** - Position of touch

## Definitions

### Modifiers

 * **S_MODIFIER_SHIFT** -           0x0001
 * **S_MODIFIER_CONTROL** -         0x0002
 * **S_MODIFIER_ALT** -             0x0004
 * **S_MODIFIER_SUPER** -           0x0008
 * **S_MODIFIER_CAPS_LOCK** -       0x0010
 * **S_MODIFIER_NUM_LOCK** -        0x0020

### Keys

 * **S_KEY_UNKNOWN** -              -1
 * **S_KEY_SPACE** -                32
 * **S_KEY_APOSTROPHE** -           39
 * **S_KEY_COMMA** -                44
 * **S_KEY_MINUS** -                45
 * **S_KEY_PERIOD** -               46
 * **S_KEY_SLASH** -                47
 * **S_KEY_0** -                    48
 * **S_KEY_1** -                    49
 * **S_KEY_2** -                    50
 * **S_KEY_3** -                    51
 * **S_KEY_4** -                    52
 * **S_KEY_5** -                    53
 * **S_KEY_6** -                    54
 * **S_KEY_7** -                    55
 * **S_KEY_8** -                    56
 * **S_KEY_9** -                    57
 * **S_KEY_SEMICOLON** -            59
 * **S_KEY_EQUAL** -                61
 * **S_KEY_A** -                    65
 * **S_KEY_B** -                    66
 * **S_KEY_C** -                    67
 * **S_KEY_D** -                    68
 * **S_KEY_E** -                    69
 * **S_KEY_F** -                    70
 * **S_KEY_G** -                    71
 * **S_KEY_H** -                    72
 * **S_KEY_I** -                    73
 * **S_KEY_J** -                    74
 * **S_KEY_K** -                    75
 * **S_KEY_L** -                    76
 * **S_KEY_M** -                    77
 * **S_KEY_N** -                    78
 * **S_KEY_O** -                    79
 * **S_KEY_P** -                    80
 * **S_KEY_Q** -                    81
 * **S_KEY_R** -                    82
 * **S_KEY_S** -                    83
 * **S_KEY_T** -                    84
 * **S_KEY_U** -                    85
 * **S_KEY_V** -                    86
 * **S_KEY_W** -                    87
 * **S_KEY_X** -                    88
 * **S_KEY_Y** -                    89
 * **S_KEY_Z** -                    90
 * **S_KEY_LEFT_BRACKET** -         91
 * **S_KEY_BACKSLASH** -            92
 * **S_KEY_RIGHT_BRACKET** -        93
 * **S_KEY_GRAVE_ACCENT** -         96
 * **S_KEY_WORLD_1** -              161  (non-US #1)
 * **S_KEY_WORLD_2** -              162  (non-US #2)
 * **S_KEY_ESCAPE** -               256
 * **S_KEY_ENTER** -                257
 * **S_KEY_TAB** -                  258
 * **S_KEY_BACKSPACE** -            259
 * **S_KEY_INSERT** -               260
 * **S_KEY_DELETE** -               261
 * **S_KEY_RIGHT** -                262
 * **S_KEY_LEFT** -                 263
 * **S_KEY_DOWN** -                 264
 * **S_KEY_UP** -                   265
 * **S_KEY_PAGE_UP** -              266
 * **S_KEY_PAGE_DOWN** -            267
 * **S_KEY_HOME** -                 268
 * **S_KEY_END** -                  269
 * **S_KEY_CAPS_LOCK** -            280
 * **S_KEY_SCROLL_LOCK** -          281
 * **S_KEY_NUM_LOCK** -             282
 * **S_KEY_PRINT_SCREEN** -         283
 * **S_KEY_PAUSE** -                284
 * **S_KEY_F1** -                   290
 * **S_KEY_F2** -                   291
 * **S_KEY_F3** -                   292
 * **S_KEY_F4** -                   293
 * **S_KEY_F5** -                   294
 * **S_KEY_F6** -                   295
 * **S_KEY_F7** -                   296
 * **S_KEY_F8** -                   297
 * **S_KEY_F9** -                   298
 * **S_KEY_F10** -                  299
 * **S_KEY_F11** -                  300
 * **S_KEY_F12** -                  301
 * **S_KEY_F13** -                  302
 * **S_KEY_F14** -                  303
 * **S_KEY_F15** -                  304
 * **S_KEY_F16** -                  305
 * **S_KEY_F17** -                  306
 * **S_KEY_F18** -                  307
 * **S_KEY_F19** -                  308
 * **S_KEY_F20** -                  309
 * **S_KEY_F21** -                  310
 * **S_KEY_F22** -                  311
 * **S_KEY_F23** -                  312
 * **S_KEY_F24** -                  313
 * **S_KEY_F25** -                  314
 * **S_KEY_KP_0** -                 320
 * **S_KEY_KP_1** -                 321
 * **S_KEY_KP_2** -                 322
 * **S_KEY_KP_3** -                 323
 * **S_KEY_KP_4** -                 324
 * **S_KEY_KP_5** -                 325
 * **S_KEY_KP_6** -                 326
 * **S_KEY_KP_7** -                 327
 * **S_KEY_KP_8** -                 328
 * **S_KEY_KP_9** -                 329
 * **S_KEY_KP_DECIMAL** -           330
 * **S_KEY_KP_DIVIDE** -            331
 * **S_KEY_KP_MULTIPLY** -          332
 * **S_KEY_KP_SUBTRACT** -          333
 * **S_KEY_KP_ADD** -               334
 * **S_KEY_KP_ENTER** -             335
 * **S_KEY_KP_EQUAL** -             336
 * **S_KEY_LEFT_SHIFT** -           340
 * **S_KEY_LEFT_CONTROL** -         341
 * **S_KEY_LEFT_ALT** -             342
 * **S_KEY_LEFT_SUPER** -           343
 * **S_KEY_RIGHT_SHIFT** -          344
 * **S_KEY_RIGHT_CONTROL** -        345
 * **S_KEY_RIGHT_ALT** -            346
 * **S_KEY_RIGHT_SUPER** -          347
 * **S_KEY_MENU** -                 348
 * **S_KEY_LAST** -                 S_KEY_MENU

### Mouse button

* **S_MOUSE_BUTTON_1** -     0
* **S_MOUSE_BUTTON_2** -     1
* **S_MOUSE_BUTTON_3** -     2
* **S_MOUSE_BUTTON_4** -     3
* **S_MOUSE_BUTTON_5** -     4
* **S_MOUSE_BUTTON_6** -     5
* **S_MOUSE_BUTTON_7** -     6
* **S_MOUSE_BUTTON_8** -     7
* **S_MOUSE_BUTTON_LAST** -      S_MOUSE_BUTTON_8
* **S_MOUSE_BUTTON_LEFT** -      S_MOUSE_BUTTON_1
* **S_MOUSE_BUTTON_RIGHT** -     S_MOUSE_BUTTON_2
* **S_MOUSE_BUTTON_MIDDLE** -    S_MOUSE_BUTTON_3

## Methods details

### isKeyPressed

 * static bool **isKeyPressed**(int key)

Return true when key is pressed.

 ---

### isMousePressed

 * static bool **isMousePressed**(int button)

Return true when any mouse button is pressed.

 ---

### isTouch

 * static bool **isTouch**()

Return true when touch is activated.

 ---

### isMouseEntered

 * static bool **isMouseEntered**()

Return true when mouse entered in canvas boundary.

 ---
 
### getMousePosition

 * static Vector2 **getMousePosition**()

Return mouse pointer position based on canvas.

 ---

### getMouseScroll

 * static Vector2 **getMouseScroll**()

Return mouse scrool information.

 ---

### getTouchPosition

 * static Vector2 **getTouchPosition**(int pointer)

Return touch position of a pointer.

 ---

 ### getTouches

 * static std::vector<Touch> **getTouches**()

Return all touches information in this moment.

 ---

 ### numTouches

 * static size_t **numTouches**()

Return number of touches in this moment.

 ---

### getModifiers

 * static int **getModifiers**()

Return modifier binary flag.

 ---

### findTouchIndex

 * static size_t **findTouchIndex**(int pointer)

Return touch index in array of [getTouches()](#gettouches)
