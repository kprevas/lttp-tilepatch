lttp-tilepatch
=

Replace graphics in an expanded LTTP ROM.

Replace a tile
-

    lttp-tilepatch [ROM file] patch \
      -o [output ROM file] \
      -p [PNG file] \
      -s [sheet number] \
      -x [x position] -y [y position]
      
The first 7 pixels of the top row of the PNG file is read as the palette
for the rest of the file.  Pixels in the rest of the file must match those
colors exactly.

By default, the modified tile sheet is moved to empty space in the ROM
starting at `0x110000`, with `0x1000` bytes reserved for each sheet.
These values can be modified using the `--exp_start` and `--exp_size`
arguments, respectively.


Dump tile sheets
-

    lttp-tilepatch [ROM file] dump
    
Each tile sheet is dumped to `stdout` using an arbitrary palette, which
can be useful for finding the right sheet.  Your shell must support color
output for this to look like anything.
    
Alternate bank locations
-

By default, the bank locations are read from `0x6790`, `0x6795`, and
`0x679A` in the ROM.

For a ROM with relocated bank locations:

    lttp-tilepatch [ROM file] 0x6890 0x6895 0x689A [dump|patch] ... 