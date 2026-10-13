# Number Notation Converter

[한국어](./NUMBER_NOTATION_CONVERTER.ko.md)

Number Notation Converter turns values written in E notation, such as `1.23457E+15` or `2.5e-4`, into readable numbers. It reads the text as exact decimal digits, so long values never lose precision, and it shows what an IEEE 754 `double` or `float` would actually store.

## Screenshot

![Number Notation Converter preview](./images/DH.DevUtil.number-notation.png)

Values go in on the left. Each result is one collapsed line on the right; an expanded line shows every form with a copy button, the stored double and float32 values, and notes.

![Learn more (EN)](./images/DH.DevUtil.number-notation_learnmore_en.png)

Learn more: explanations in the page, switchable between EN and 한국어.

## Features

- Convert many values at once. Separate them with new lines, tabs, semicolons, or a comma followed by a space.
- Accept these input forms:
  - E notation: `1.5E3`, `1.5e+3`, `-2.5e-4`, `.5e2`
  - Powers of ten: `1.5 × 10^3`, `1.5*10**3`, `10³`
  - Digit separators: `1,000,000`, `1 000 000`, `1_000_000`, `1'000'000` (C++14)
  - Language suffixes `f`, `d`, and `m`
  - `0x`, `0b`, and `0o` integers, and hex floats such as `0x1.8p3` or `0x1.8p3f`
- Show each value in these forms, each with a copy button:
  - Plain, with every digit
  - Grouped, with a selectable separator: comma, space, underscore, or apostrophe
  - Scientific (`1.5E+3` and `1.5 × 10³`)
  - Engineering notation, with the exponent a multiple of 3
  - SI prefix (`250 µ`, `4.7 k`)
  - Korean units (만, 억, 조, 경 … 극)
- Count significant digits, integer digits, and decimal places.
- Show the exact value that a `double` (binary64) and a `float32` (binary32) would store, the shortest text that reads back to the same value, and the rounding difference, overflow, or underflow.
- Warn when an integer exceeds 2<sup>53</sup> − 1, the largest integer that JavaScript `Number` and many JSON parsers keep exactly.
- Note when a value looks like Excel's display of a long number, since the digits Excel did not store cannot be recovered.
- Explain E notation, floating-point storage, large integer IDs, Excel behavior, language literals, and Korean units in a Learn more section that switches between English and Korean.
- Process everything in the browser without external libraries, network requests, or persistent storage. The Learn more language choice is the only setting the browser remembers.

## How to use

1. Open [Number Notation Converter](../tools/DH.DevUtil.number-notation.html) in a modern browser. The HTML file works on its own.
2. Type or paste values into **Values**, or select **Load examples**. Results update as you type. Each result is collapsed to one line that shows the input and its grouped value, or the error message. Select a line to expand it, or use **Expand all** and **Collapse all**.
3. Select a separator for the **Grouped** row in **Digit grouping**. Use the apostrophe for C++14 literals or the underscore for C#, Java, JavaScript, and Python literals.
4. Select **Copy** on any row, or **Copy all plain values** to copy every plain result, one per line.

## How the conversion works

- Input text is parsed into a sign, a string of decimal digits, and a power of ten. Every decimal form is produced by moving the decimal point, so results stay exact even for values longer than 17 digits.
- Plain output is limited to 1,200 characters. Longer values, such as `1e5000`, are shown in the scientific forms only.
- The IEEE 754 results are computed with integer arithmetic using round to nearest, ties to even. They were cross-checked with 20,000 random values against the browser's `Number()` and `Math.fround()`.
- The stored value is the exact decimal expansion of the binary value. For example, `0.1` as a double is `0.1000000000000000055511151231257827021181583404541015625`.
- The shortest text is the shortest decimal that converts back to the same stored value. For a double it is the JavaScript `String()` output.

## Notes and limits

- Exponents are limited to ±1,000,000,000 for decimal input and ±100,000 for hex floats.
- `Infinity` and `NaN` are rejected because they are not finite numbers.
- Commas and spaces are accepted only as thousands separators in the integer part, in groups of three such as `1,234,567`. Values such as `1,5` or `1.234,56` are rejected because the decimal comma used in some locales is not supported.
- A space between digit groups is read as grouping, so `100 200` is one value, 100200, and the result notes this. Put separate values on separate lines.
- The apostrophe (C++14) and underscore (C#, Java, JavaScript, Python) may appear between any two digits of the integer or fraction, but not next to the decimal point or in the exponent.
- The `m` suffix (C# `decimal`) is accepted, but C# decimal arithmetic is not simulated.
- The Excel note is a hint based on the display pattern; the tool cannot know where the text came from.
