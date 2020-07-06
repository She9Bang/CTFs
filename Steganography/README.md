<a name="Scanning-and-detection"></a>Scanning and detection :
File image.jpg : check which type of file it is 
String file.txt : gets the hidden text (by default defaut, seraches for printables (ASCII)) 
exiftool file.jpg : read the metadata of the file (size, permission, width, height...etc) 
binwalk -e file : extracts hidden folders (Ignore the "zlib" when it's PNG) 
hexdump -C file : literally...hex dmp x) 
foremost -i file : extracts data based on header, footer, and inernal data structure (isolate the file from other embedded stuff) 
Trying steghide on the file is worth also worth it : 
steghide extract -sf file.jpg
to crack the passphrase : 
stegcracker file.jpeg word_list.txt

<a name="images"></a>For images :
zsteg file.png :  detects LSB data in png and bmp (-h for options) 			 
GIMP : play with colors and contrasts..RGB channels ! 
Stegsolve : applies many color filters on the image
Download then launch it with java -jar stegsolve.jar 
Check for differences : reverse google image search, get the exact image (same dimensions) then use 
compare challl_image.png original.png -compose src diff
print the values of the different pixels, convert them to HEX and decode :D 
Hiding a picture inside another : Every JPEG file starts from the binary value ‘0xFFD8‘ and ends by the binary value ‘0xFFD9‘, so if there is additional data after the EOF, we need to check on that ! 
Thumbnails : A thumbnails is the preview of the picture ( a smaller version of the picture that is embedded inside of it) 
we can extract the thumbnails with exiftools
exiftool -b -ThumbnailImage file.jpg > thumbnail.jpg

