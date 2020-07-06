<h2>Scanning and detection :</h2>
<p>File image.jpg : check which type of file it is </p>
<p>String file.txt : gets the hidden text (by default defaut, seraches for printables (ASCII))  </p>
<p>exiftool file.jpg : read the metadata of the file (size, permission, width, height...etc)  </p>
<p>binwalk -e file : extracts hidden folders (Ignore the "zlib" when it's PNG)  </p>
<p>hexdump -C file : literally...hex dmp x)  </p>
<p>foremost -i file : extracts data based on header, footer, and inernal data structure (isolate the file from other embedded stuff)  </p>
<p>Trying steghide on the file is worth also worth it :  </p>
<p>steghide extract -sf file.jpg </p>
<p>to crack the passphrase :  </p>
<p>stegcracker file.jpeg word_list.txt </p>

<h2>For images :</h2>
<p>zsteg file.png :  detects LSB data in png and bmp (-h for options) 	 </p>		 
<p>GIMP : play with colors and contrasts..RGB channels !  </p>
<p>Stegsolve : applies many color filters on the image </p>
<p>Download then launch it with java -jar stegsolve.jar  </p>
<p>Check for differences : reverse google image search, get the exact image (same dimensions) then use  </p>
<p>compare challl_image.png original.png -compose src diff </p>
<p>print the values of the different pixels, convert them to HEX and decode :D  </p>
<p>Hiding a picture inside another : Every JPEG file starts from the binary value ‘0xFFD8‘ and ends by the binary value ‘0xFFD9‘, so if there is additional data after the EOF, we need to check on that !  </p>
<p>Thumbnails : A thumbnails is the preview of the picture ( a smaller version of the picture that is embedded inside of it)  </p>
<p>we can extract the thumbnails with exiftools </p>
<p>exiftool -b -ThumbnailImage file.jpg > thumbnail.jpg </p>

