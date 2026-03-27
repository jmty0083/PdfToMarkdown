# PdfToMarkdown

A WPF desktop application for Windows that converts PDF pages to Markdown files, preserving headings, lists, bold/italic text, and embedded images.

## Features

- **Drag & drop or file picker** — drop a PDF onto the window or click to browse
- **Page selection** — choose individual pages or convert all at once
- **Structure inference** — headings (`#`–`####`), bullet lists, numbered lists, and inline bold/italic are detected from font size and style; no OCR required
- **Image extraction** — embedded images are saved to an `_assets/` folder and referenced inline in the Markdown
- **Two output modes** — all selected pages combined into one `.md` file, or one file per page
- **Progress bar** — live conversion progress across multi-page documents

## Requirements

- Windows 10 or later
- [.NET 8 Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) (Windows Desktop)

## Building

```
dotnet build PdfToMarkdown/PdfToMarkdown.csproj
```

Or open the project in Visual Studio 2022+ and press F5.

## Usage

1. Launch `PdfToMarkdown.exe`
2. Drop a PDF file onto the window, or click the drop zone to open a file dialog
3. Select the pages to convert (all pages are selected by default)
4. Choose an output folder
5. Optionally check **One file per page** to split the output
6. Click **Convert**

Output files are written to the selected folder:

| Mode | Output |
|---|---|
| Combined | `{pdf-name}.md` + `{pdf-name}_assets/` |
| Per page | `{pdf-name}_page_N.md` + `{pdf-name}_page_N_assets/` per page |

## Notes

- Text extraction relies on the PDF's embedded font data — scanned PDFs (image-only) will produce empty output
- Heading levels are inferred by comparing each line's font size to the most common body font size in the document
- Images are saved as PNG where possible, falling back to JPEG or raw bytes
