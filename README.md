
# Simple home row mods for MacOS split keyboards.
2022-11-28


The definitive guide to setting up Home Row Mods is https://precondition.github.io/home-row-mods

But it's also REALLY complicated and I feel it doesn't need to be.


## My Setup: CAGS SGAC

My use case which is also the same for most people I know is to add Mac modifiers to the home row on Querty.
Thats it.

"A" long pressed is "Control"
"S" long pressed is "Alt/Option"
"D" long pressed is "GUI/Cmd"
"F" long pressed is "Shift"

And it's mirrored on the right hand.

In the QMK configs you wrap ASDF and JKL; with these codes in keymap.c:
 - CTL_T()
 - OPT_T()
 - CMD_T()
 - SFT_T()

Third row now looks like this (wrapped to make it easier to see.
I have a split keyboard, so H is the right hand.

```C
const uint16_t PROGMEM keymaps[][MATRIX_ROWS][MATRIX_COLS] = {
// ...
[_QWERTY] = LAYOUT(
     // ...
     KC_LCTL, CTL_T(KC_A), OPT_T(KC_S), CMD_T(KC_D), SFT_T(KC_F),    KC_G, 
     KC_H,    SFT_T(KC_J), CMD_T(KC_K), OPT_T(KC_L), CTL_T(KC_SCLN), KC_QUOT,
     // ...
     )
// ...
}
```

And add to config.h
```C
#define IGNORE_MOD_TAP_INTERRUPT
```
