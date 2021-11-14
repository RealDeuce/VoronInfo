# VoronInfo
A collection of notes regarding my Voron 3D Printer(s)

## Book of Ellis
And Doc declared, "Thou shalt remain perfect in thine PIF, neither overextruding nor underextruding, with thine infill attached solidly and overhangs thou printest shalt be cleane."  And there was much wailing and knashing of teeth, for we did not know how to tune our systems.  Then Ellis proclaimed "Get thee to mine Guthub where the dark mysteries of tuning are laid forth."  When we did, our prints prospered, and the PIF backlog became as naught. 
[Book of Ellis](https://github.com/AndrewEllis93/Print-Tuning-Guide)

https://discord.com/channels/460117602945990666/472450547534921729/900168232667844708

## Selecting RRI
Because Vorons other than Switchwire have Z endstops separate from their probe, they can benefit from using the relative_reference_index setting (RRI). This setting allows the probe z_offset to be auto-calculated using the configured position_endstop value.  The chosen RRI therefore should be the one where position_endstop is most accurate.

The accuracy of position_endstop is impacted by changes in the printer as it heats up.  Any axis with a rail mounted on the top or bottom of the extrusion will bow vertically and while backers mostly mitigate this, there is still an effect with backers in use.  Because of this, position_endstop should be calibrated with any axis that has a rail on the top or bottom of the extrusion located at the end of it's travel.  For any other axis, the position should be the mesh probe point closest to the endstop to minimize any other sources of variance.  For an axis that does not change the distance from the nozzle to the endstop, the centre of the bed should be chosen.  On a V2, this means one of the four corners.  For Trident, this means the probe point from the back row closest to the endstop.  Switchwire does not benefit from setting RRI.

Once position_endstop is calibrated at the best mesh probe point, the relative_reference_index for that point should be configured in printer.cfg.

References: https://www.klipper3d.org/Bed_Mesh.html#the-relative-reference-index
            https://github.com/Deutherius/Gantry-bowing-induced-Z-offset-correction-through-relative-reference-index#how-the-hell-does-that-have-anything-to-do-with-z-offset

Klicky can directly measure position_endstop at any point on the bed based on the datasheet of the microswitch that is used.  This point should be the relative_reference_index point.  If it currently isn't I'll do a pull request to make it so after I install a Klicky and can test it.

https://discord.com/channels/460117602945990666/708793715480854560/909419415253184523
