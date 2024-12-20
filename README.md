# Brother PT-H110 Label Maker

I'm interested in repurposing this Brother label maker for its keyboard and display. Is it hackable? I guess we'll find out. From @furrtek, we already have a head start: https://github.com/furrtek/PTouchHH. Seems like the microcontroller is pretty much completely locked out. Could bother with double-checking? TBD.


![](Photos-001/PXL_20241219_235555626.jpg)
![](Photos-001/PXL_20241220_001044906.jpg)

## Main Board


![](Photos-001/PXL_20241220_001539005.jpg)

I was able to scan the back of the board since it's flat. I'd need to remove some components from the front to do the same there. Even with the small deviation from flatness at the bottom, the focus goes slightly out in this scan.

![](MainBoardBack.png)

## Notable Parts

- [R5F100MHAFB#V0](https://www.mouser.com/datasheet/2/698/r01ds0131ej0370_rl78g13-3083289.pdf) - Renesas - 16-bit microcontroller, 192KB/16KB, in 80LFQFP
- "UTC" 8-DIP chip - Chinese PMIC probably for general power management or battery charging? See e.g. [this forum thread](https://forum.allaboutcircuits.com/threads/datasheet-for-utc-7608d-i-c.187103/) for a similar part
- [W25Q40CL](https://www.mouser.com/datasheet/2/949/w25q40cl_e_07282017-1489768.pdf) - Windbond - 4Mb SPI Flash
- MTG-F014013 - Custom LCD display, guessing about the first dash in the part number, 8-pin connection out. Compare with e.g. the [MTG-E8619](https://www.elecok.com/panel-5-7-inch-320-240-industrial-lcd-display-module-mtg-e8619.html)

The off-chip Flash memory might be a fortunate circumstance, the unit Furrtek analyzed didn't have one. Could also be locked out or a dead end, we'll see.

The microcontroller is one of the 80-pin variety (see p. 41 of datasheet for block diagram).

Something that's going to be interesting: the keyboard being part of the main board means I can't just replace the main board, but will have to piggy-back. Not sure how difficult that's going to be. I'm not that familiar with keyboards and displays, don't really know what to expect.

## Keyboard Matrix

I traced out the keyboard matrix. Whether that was really necessary, who's to say...

![](keyboard_traces.png)

The matrix below maps the pins on the main MCU to the 62 buttons (60 keys, since space is actually three buttons). The column represents the top pad, the row represents the bottom pad. For example the `A` key is pin 28 (top) and pin 37 (bottom).

![](KeyboardMatrix.png)

