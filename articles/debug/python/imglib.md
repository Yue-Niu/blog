## read/write uint16 in cv2
**SAVE:** as long as the data is in uint16 format, cv2.imwrite can write uint16 data into file.
**READ:** by default, imread will take data in the file as *cv2.IMREAD_COLOR*, which is 8-bit data. To load a uint16 data, this flag should be set as *cv2.IMREAD_UNCHANGED*.

