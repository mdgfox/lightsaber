# Lightsaber

Fun project to celebrate 4'th of may

## How It Works: Color & Force Affinity Generation

The application generates a unique lightsaber crystal resonance (color and Force side) based on a client-side digital fingerprint (hash). Here is how the algorithm works:

1. **Fingerprint Collection:** 
   The app gathers various browser and environment parameters into a single string:
   * User Agent (OS and browser details)
   * Screen resolution and color depth
   * Timezone offset
   * Hardware concurrency (CPU cores) and device memory

2. **Hash Generation:** 
   The combined string is processed through a hashing algorithm (similar to Bernstein's hash) to produce a unique hexadecimal identifier (e.g., `0x7B4E29F`). This hash is saved in `localStorage`.

3. **Hue & Color Mapping:** 
   * The numeric value of the hash is divided modulo 360 (`numericValue % 360`) to get a precise angle on the **HSL color wheel** (`0°` to `359°`).
   * Saturation is fixed at **90%** and Lightness at **50%** to ensure a vibrant, glowing plasma effect (pure black and pure white are intentionally excluded).

4. **Side Affinity:** 
   Based on the resulting hue and hash parity, the script determines your alignment:
   * **Dark Side** (for specific red/crimson thresholds under even hash values)
   * **Light Side** (for blue, cyan, and green spectrums)
   * **Gray / Balanced** (for intermediary custom shades)

## Tech Stack
* Pure HTML5, CSS3 (Custom properties, Flexbox, Glow effects via box-shadow, Isolation and Blend Modes)
* Vanilla JavaScript (Web Audio API for sound effects, custom hashing logic)
