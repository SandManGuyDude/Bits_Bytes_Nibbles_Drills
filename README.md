# Bits_Bytes_Nibbles_Drills
Practice game for C unions, bytes, nibbles and bits.
A browser game for practicing how a C `union` lets you read and change one 32-bit integer through its bytes, nibbles and individual bits.

**Play it here:** https://SandManGuyDude.github.io/Bits_Bytes_Nibbles_Drills/

## Why I made this

In my C/C++ class we worked with a `myInt` union where the same 4 bytes of memory can be reached as:

- `x.value`, the whole 32-bit number
- `x.bytes.byte0` … `byte3`, one byte each
- `x.bytes.byteN.nibbles.nibble0` / `nibble1`, one hex digit each
- `x.bytes.byteN.bits.bit0` … `bit7`, one bit each

On quizzes, `x.value` is shown in hex and you're asked something like *"change that E to an F."* To answer, you have to know exactly which byte, nibble or bit holds that digit. This game drills that skill.

## How it works

`x.value` is shown as 8 hex digits, and each name points to a fixed spot:

```
x.value =  0x   D    1    2    2    1    3    0    4
               └─byte3─┘ └─byte2─┘ └─byte1─┘ └─byte0─┘
               nib1 nib0 nib1 nib0 nib1 nib0 nib1 nib0
```

- **byte0 is on the right** and byte3 is on the left, because x86 PCs are little-endian. This is the most common mistake.
- **nibble0 is the right digit** of a byte, and nibble1 is the left digit.
- **bit0–bit3** are in the right digit (worth 1, 2, 4, 8), and **bit4–bit7** are in the left digit.

## Game modes

| Mode | What you do |
|---|---|
| **Edit it** | A digit is highlighted. Type real C code to change it. Some rounds limit you to nibbles only, bits only or byte `.value` only. |
| **Trace it** | You're shown one line of C. Predict the new `x.value`. |
| **Locate it** | Multiple choice: which field holds the highlighted digit? |

Wrong answers explain what went wrong, for example when you counted bytes from the left instead of the right. Turn off **Show memory map** to practice without the labels.

## Running it

It's a single HTML file with plain JavaScript, so there's nothing to install. Open `index.html` in any browser, or use the GitHub Pages link above.

## Credits

- The `myInt` union and struct layout come from **Professor Liviu Oniciuc's** course at Cal Poly Pomona and are used with his permission.
- I built this with help from [Claude](https://claude.ai), an AI assistant by Anthropic. I designed the idea and tested it, and Claude wrote most of the code.
