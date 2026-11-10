# Markdown Viewer for Windows

A lightweight, portable Markdown file viewer packaged as a single HTA application. It provides a convenient way to read `.md` and `.markdown` documents without installing an editor or running a web server.

## Features

- Clean rendering of Markdown documents
- Automatically generated table of contents based on headings
- Permanently visible contents panel
- Resizable contents panel with a draggable divider
- Automatic wrapping of long entries and scrollbars when needed
- Open documents with the toolbar button
- Validation of selected files (`.md` and `.markdown` only)
- Create or remove file associations directly from the application
- Per-user file association stored under `HKEY_CURRENT_USER`
- Automatic localization based on the Windows user language
- English fallback when the detected language is not supported
- Runs from a read-only location
- No external libraries, internet connection, or supporting files required

## Supported languages

- Czech
- English
- Polish
- German
- Ukrainian
- Russian
- Simplified Chinese
- French

## Running the application

Download `MarkdownViewer.hta` and open it by double-clicking the file. Use the **Open MD** button to select a document.

Markdown Viewer is portable and can be stored on a network drive or in a directory where the application has no write permission. It does not create temporary or supporting files next to the application.

## File associations

The **Associate .MD** button registers Markdown Viewer for `.md` and `.markdown` files. The change is written only to the current user's registry and does not require administrator privileges.

On the first double-click, Windows may ask you to confirm that the document should open with **Microsoft (R) HTML Application host**. Subsequent documents should open directly.

Use the same button to remove the association. The application attempts to restore the previous `.md` association when one was available before registration.

## Supported Markdown elements

The viewer supports common elements used in documentation, including:

- Headings
- Paragraphs and line breaks
- Bold and italic text
- Links and images
- Ordered and unordered lists
- Inline code and fenced code blocks
- Block quotes
- Tables
- Horizontal rules
- Task lists

Relative image paths are resolved against the directory containing the open document.

## Requirements

- Windows with `mshta.exe` and the MSHTML component available
- HTA execution permitted by the system policy

The application uses the Windows MSHTML component rather than a modern browser engine. Rendering may therefore differ from the complete CommonMark or GitHub Flavored Markdown specifications.

## Adding another language

Translations are kept together in the `translations` object inside the HTA file. To add a language, copy an existing block and assign its two-letter ISO 639-1 language code. Every language block must contain the same property names.

Non-ASCII characters in translations are written as JavaScript Unicode escape sequences in the `\uXXXX` form.