# Notes

**This is a beta version, it’s not been QA-ed extensively in lesser-known Reading Systems and Kindle.**

## Description

- Format: EPUB 3.0.1
- Embedded fonts: YES (Average Mono for code since Kobo eReaders doesn’t ship with a monospace)
- TOC/Landmarks: YES
- NCX/Guides: YES (for backwards compatibility)
- Inline TOC: YES (in anticipation of Kindle conversion)
- HTML5 tags: YES
- EPUB Vocab (`epub:type`): YES
- Linked index: YES
- a11y metadata: YES
- iBooks metadata: YES
- Progressive enhancement (CSS): YES
- ePubCheck 4.0.2: OK
- Backwards compatibility: should be OK

## Important notes

- ET Book has rendering issues in eInk and Adobe’s RMSDK so it was not used
- Progressive enhancement is achieved using feature queries (`@supports`), Adobe’s RMSDK will ignore the entire stylesheet if you get rid of them
- Fallbacks provided for rgba values
- Quotes (`blockquote`) implemented using SVG + `background` property (will degrade gracefully in EPUB 2)
- Backwards compatibility should be OK: worked without any issue in legacy apps/devices I could QA but some may use an older version of RMSDK with their specifics bugs