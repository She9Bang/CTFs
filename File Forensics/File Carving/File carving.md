-File carving is a process of searching for files in a data stream based on knowledge of file formats rather than any other metadata. 
It's used in computer forensics to extract data without the assistance of the file system that originality created the file ( in the absence of filesystem metadata) 

This is usually done by examining the header (the first few bytes) and footer (the last few bytes) of a file.

The most common general file carving technique is Header-footer or header-“maximum file size” carving which Recover files based on known headers and footers or maximum file size

  JPEG—”\xFF\xD8″ header and “\xFF\xD9” footer
  
  GIF—”\x47\x49\x46\x38\x37\x61″ header and “\x00\x3B”


How to carve files :
1- Hex editor
If JPEG, search for "FFD8FFE0" and get Data until "FFD9"
Now we copy the whole block of data with header and trailer and store it as a new file.
  
2- with scalpel :
$ sudo apt-get install scalpel
Once scalpel is installed you need to do text editing. By default scalpel utility has its own configuration file in ‘/etc‘ directory and full path is “/etc/scalpel/scalpel.conf” . You can notice that everything is commented out (#). So before running scalpel you need to uncomment the file format that you need to recover. However uncomment the entire file is time consuming and will generate a huge false results.

scalpel -c scalpelConfig.txt image.jpg -o output

3- with tools like Autopsy 
