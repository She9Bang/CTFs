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

<h2> PDF Analysis : </h2>
<h5>1- run pdf-parser to get a summary about what the pdf contains </h5>
  <p>pdf-parser --stats file.pdf </p>
 <p>If in the output we hvae something like " /Embeddedfile 1: 3"</p>
 <p>it means there's exactly 1 Embeddedfile inside, with an object id of 3</p>

<h5>2-Extract the embedded file : </h5>
   <p>pdf-parser --object 3 --raw --filter file.pdf > out</p>
 <p>Print the extracted file </p>
   <p>cat out</p>
 <p>If it's some base-64 encoded string, decode it and put the output on another file:</p>
   <p>base64 -di  out > out2</p>
 <p>Now check the type of the file</p>
   <p>File out2</p>
 <p>If it's a JPEG for exemple</p>
   <p>mv out2 out3.jpeg </p>

