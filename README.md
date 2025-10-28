# Color Mixer Pro: Application Documentation

An interactive web application for mixing two HEX colors at a specified ratio, powered by vanilla JavaScript and styled with Tailwind CSS.

---

## 🚀 Overview

**Application Name:** Color Mixer Pro
**File:** `index.html` (or similar)
**Purpose:** Allows users to select a **Base Color** and a **Mix Color**, adjust the blending intensity (**percentage**), view the resulting mixed color in **HEX, RGB, and HSL** formats, and save their favorite mixes to a history panel.

---

## 🗃️ File Structure & Dependencies

This is a single-file application with external dependencies.

| File | Description | Notes |
| :--- | :--- | :--- |
| `index.html` | The main HTML structure, CSS styles, and all JavaScript logic. | Contains all code provided. |
| `color.png` | Favicon for the browser tab. | **Required** for the `<link rel="icon"...>` to work. |

### External Dependencies (CDNs)

| Resource | Type | URL/Description |
| :--- | :--- | :--- |
| **Tailwind CSS** | Styling | `https://cdn.tailwindcss.com` |
| **Font Awesome 6.4.2** | Icons | `https://cdnjs.cloudflare.com/.../all.min.css` |
| **Google Font (Inter)**| Typography | `https://fonts.googleapis.com/css2?...` (via `@import` in `<style>`) |

---

## ✨ Features

### Color Selection
* **Base Color:** Selectable via a color picker (`<input type="color">`) or a HEX code input. Comes with a palette of four preset colors.
* **Mix Color:** Selectable via a color picker or a HEX code input. Comes with a palette of four primary/utility color presets (Red, Green, Blue, White).

### Mixing Controls
* **Blend Intensity:** A slider (`<input type="range">`) to control the mixing ratio from **0%** (100% Base Color) to **100%** (100% Mix Color).
* **Quick Buttons:** 25%, 50%, and 75% ratio buttons for fast adjustments.

### Result & Export
* **Mixed Color Display:** Shows the resulting color, along with its **HEX**, **RGB**, and **HSL** values.
* **Clipboard Copying:** Buttons to quickly copy the resulting HEX or RGB codes.
* **History:** Users can **Save Color** to the local history (max 10 items) and click on a history item to restore the mixing parameters.
* **Actions:**
    * **Random Colors:** Sets both Base and Mix colors to random HEX values and a random ratio.
    * **Reset Colors:** Returns colors and ratio to their initial default values.
    * **Export Palette:** Copies a simple 5-color shade palette (derived from the base color) as a JSON object to the clipboard.

### UX/Accessibility
* **Modern Styling:** Utilizes custom CSS variables and Tailwind classes for a clean, responsive, and modern card-based layout.
* **Toast Notifications:** Provides feedback for saving, copying, and action completion.
* **Keyboard Shortcuts:**
    * `R`: Reset Colors
    * `S`: Save Color
    * `C`: Copy HEX
    * `E`: Export Palette

---

## 🛠️ Key JavaScript Functions

| Function | Description |
| :--- | :--- |
| `mixColors()` | Core logic: Calculates the mixed color by blending the RGB values of `baseColor` and `mixColor` based on the `percentage`. Updates the display elements. |
| `hexToRgb()`, `rgbToHex()` | Utility functions for color format conversions. |
| `rgbToHsl()` | Converts RGB to HSL for display in the result panel. |
| `saveToHistory()` | Stores the current mixed color, base color, mix color, and percentage in the `appState.history` array. |
| `randomizeColors()`, `resetColors()` | Control functions for managing the state. |
| `copyToClipboard()` | Uses the `navigator.clipboard` API to copy the color code. |

---

## 📝 Initial State

| State Variable | Value | Description |
| :--- | :--- | :--- |
| `baseColor` | `#ff6b6b` | Initial Base Color (Reddish-Pink). |
| `mixColor` | `#ff0000` | Initial Mix Color (Pure Red). |
| `percentage` | `25` | Initial blend ratio (25% Mix Color / 75% Base Color). |
| `mixedHex` | `#ff35b5` | Initial result of the mix. |
| `history` | `[]` | Empty history array. |
