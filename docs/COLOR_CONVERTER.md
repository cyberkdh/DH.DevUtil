# Color Converter

[한국어](./COLOR_CONVERTER.ko.md)

Color Converter converts common color formats, calculates WCAG contrast, and explains how RGB, HSL, HSV, and OKLCH describe color.

## Features

- Convert `#RGB`, `#RGBA`, `#RRGGBB`, and `#RRGGBBAA` to RGB, HSL, HSV, and OKLCH.
- Preserve alpha in HEX and CSS output.
- Check foreground/background contrast against WCAG 2 AA and AAA thresholds.
- Place the WCAG controls/results on the left and a right-side interface preview on desktop; show small, body, large, and heading text sizes plus link, button, and input styles using the selected foreground/background colors.
- Switch the interface and learning guide between English and Korean.
- Process all values locally in a standalone HTML file.

## How to use

1. Open [Color Converter](../tools/DH.DevUtil.color-converter.html) in a modern browser.
2. Enter a HEX color or use the color picker.
3. Read the converted formats and OKLCH values.
4. Enter foreground and background colors to check contrast.
5. Use **Apply to foreground**, **Apply to background**, or **Swap contrast colors** to reuse the selected color in the WCAG checker.
6. In **Optimized contrast colors**, choose a target ratio, compare the best black/white, neutral gray, or hue-preserving suggestions, then apply one to foreground or background.
7. Use the suggested palette to see current Foreground/Background colors together with Primary, Surface, Dark, and Canvas colors. Every palette box also shows its actual or suggested counterpart color.

## Important details

- RGB channels use 0–255. HSL uses hue, saturation, and lightness; HSV uses hue, saturation, and value.
- OKLCH is calculated from the input sRGB color. It is useful for perceptual adjustments, but the final sRGB color should still be checked for gamut clipping and accessibility.
- WCAG contrast uses relative luminance. Normal text needs 4.5:1 for AA and 7:1 for AAA; large text needs 3:1 and 4.5:1.
- Contrast preview uses the RGB channels of the entered colors; alpha compositing against an additional background is not simulated.
- Hue-preserving recommendations adjust HSL lightness while keeping the current hue and saturation as close as possible; they are practical suggestions, not a guarantee of color harmony.

## Privacy

All processing happens in the current browser tab. The tool has no server endpoint, external library, upload control, or persistent input storage. The selected interface language may be saved in `localStorage`.
