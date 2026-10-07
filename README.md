# Barcode Generator

A lightweight, single-file barcode generator that runs entirely in the browser. Enter text or a number, pick a format, and generate a scannable barcode you can copy straight to your clipboard as an image.

No build step, no server, no dependencies to install — just open the HTML file.

## Features

- **Multiple formats** — Code 128, Code 39, EAN-13, UPC, ITF, and MSI
- **Instant generation** — renders to a `<canvas>` as you click *Generate* (or press <kbd>Enter</kbd>)
- **Copy to clipboard** — copies the barcode as a PNG image, ready to paste anywhere
- **Input validation** — shows a clear message when the input doesn't match the selected format
- **Zero install** — a single `.html` file with no local dependencies

## Usage

1. Open [`BarCode.html`](BarCode.html) in any modern browser (double-click it, or serve it locally).
2. Choose a barcode format from the dropdown.
3. Type your text or number into the input box.
4. Click **Generate** (or press <kbd>Enter</kbd>).
5. Click **Copy to Clipboard** to copy the barcode as an image.

### Format notes

Each symbology has its own input rules — for example, EAN-13 expects 12–13 digits and UPC expects 11–12 digits. If the input is invalid for the chosen format, an error message appears instead of a barcode.

## How it works

Barcode rendering is handled by [JsBarcode](https://github.com/lindell/JsBarcode), loaded from a CDN:

```html
<script src="https://cdn.jsdelivr.net/npm/jsbarcode@3.11.6/dist/JsBarcode.all.min.js"></script>
```

Because the library is loaded from a CDN, an internet connection is required the first time the page loads. The "Copy to Clipboard" feature uses the [Clipboard API](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API), which requires a secure context (`https://` or `localhost`) in most browsers.

## Running locally

You can just open the file directly, but serving it over `http://localhost` is recommended so clipboard copy works reliably:

```bash
# Python 3
python -m http.server 8000
```

Then visit `http://localhost:8000/BarCode.html`.

## License

Released under the [MIT License](LICENSE).

## Credits

Built with [JsBarcode](https://github.com/lindell/JsBarcode) by Johan Lindell.
