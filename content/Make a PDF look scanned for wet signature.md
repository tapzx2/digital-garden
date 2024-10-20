---
tags:
  - permanent_note
  - public
---
## When You Need a Wet Signature
Sometimes agencies/corporations/institutions want a "wet" signature on a piece of paper. If you can get away with the low resolution [Mac Preview version](https://support.apple.com/en-in/guide/preview/prvw35725/mac#Create-and-use-signatures), good for you! Can't? Just print, sign, scan send. But no printer? Don't speak the local language? Feeling cheap? Have to get a document done at 2am? Here's how I did it.
## Add High Resolution Signature to PDF Using Preview
1. Sign a piece of paper
2. Take a photo of your signature
3. Use adobe express to remove the background https://new.express.adobe.com/tools/remove-background#
4. Open in signature in Preview, reduce image size to 500 width 300 dpi.
5. Add images to existing PDF with Preview

```
Do as follows:

- Open the image you want to paste in Preview.app
- Select All (Command-A)
- Copy (Command-C)
- Paste (Command-V)

Now you have a copy of your image pasted above your old image. This is apparently meaningless, but the new copy is not just an image, but an object.

- Click on the new image (round blue corners appear, no marching ants)
- Copy (Command-C)
- Paste on your PDF document. The image is an object, moveable and resizable. The original PDF is still a PDF, editable and all.

```

**Note** There is the extra, non-obvious step of "pasting" the source image into the source image file _before_ you can paste it into the target file.
## Make It Look Scanned
If you want to make it look scanned, you can use command line tools.
1. `brew install imagemagick poppler`
2. `convert -density 130 input.pdf -colorspace Gray ouput.pdf`
There are options to make it even more authentic, but I ended up with very heavy pdf files.
- Super PDF Scan Code
## Automate It
Finally, if you need to do this frequently, automate it.
https://bradt.ca/blog/how-to-make-a-pdf-look-scanned-imagemagick-automator-macos/
