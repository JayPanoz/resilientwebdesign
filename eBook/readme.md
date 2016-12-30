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

## InDesign

I’ve added an InCopy file to kickstart the InDesign process (Thanks Pandoc!). You can [download it here](https://github.com/JayPanoz/resilientwebdesign/blob/master/eBook/ResilientWebDesign.icml).

Import it in your InDesign template and it should make the process a lot faster since 90% of contents are already styled (paragraph and character styles), image objects are anchored, etc.

However… what you should pay attention to:

- hyperlinks: they’re from the EPUB version so internal links won’t work in InDesign. Unsync the InCopy file first (Links panel > right click) or you won’t be able to erase them in hyperlinks panel;
- small caps: unfortunately, Pandoc doesn’t support them unless the EPUB file is modified and `span style="font-variant: small-caps"` is used but it should be fast reimplementing them in InDesign with GREP;
- figures: the biggest images should be used for best quality (print), captions have to be styled using a dedicated paragraph style;
- “Heading 1” is actually “Heading0”, “Heading 2” is “Heading1”, etc. (styles can be renamed though);
- “NumList > first” and “BulList > first” are normal, they allow for reset (or else list num starts where the previous list finished;
- you can get rid of “Default” character style and replace it with “None”.

Code, lists, blockquote, etc. are OK. It’s just about modifying the paragraph and character styles.

The ET Book typeface with ligatures can be [downloaded in OTF format](https://github.com/adactio/et-book/tree/65f78029d378dea4a864a395933988b49adf0be2/et-book-ligatures-enabled).

### Conversion

Should you want to alter the EPUB file so that small-caps are exported, here is how you convert the EPUB file to InCopy using [Pandoc](http://pandoc.org).

```
pandoc -s -f epub -t icml -o [path/to/ResilientWebDesign.icml] [path/to/ResilientWebDesign.epub]
```

And that’s it.