Upload profiles
==================
2017-04-28



A system to handle file uploads in a modular architecture.



[![upload-profiles.png](https://s19.postimg.org/3lr4t9bs3/upload-profiles.png)](https://postimg.org/image/thavcgdlr/)



This system's main goal is to prevent the user form changing the upload parameters.

It does so by passing only an abstract identifier, which only the application knows how to handle.

Each identifier identifies a profile, which contains the information necessary to handle an upload.



Synopsis
=============

The following synopsis describes the figure shown at the top of this document.

1. A page is displayed, which contains a drop zone widget, so that the user can upload a file.
2. The drop zone is powered by a javascript library, which requires some params.
3. The params are taken from a so-called "upload profile", which is accessed via a profileId.
4. The user then drops a file into the drop zone.
5. Server side, a script will handle the upload (place the file on the server).
6. In order to do that, the script accesses the second part of the upload profile, which is a part dedicated for the server side.
7. The script places the file on the server successfully, this is the end of the synopsis.



A profile example
========================


A profile could look like this.



- ?maxFileSize: int, size in M, intended to be checked application side
- ?acceptedFiles: array of accepted mime types or file extensions, intended to be checked application side

- targetDir: the full path to the directory containing the items
- ?checkUser: null|callback, if callback, returns boolean: whether or not the user is granted the permission to upload to that dir.
                            If not, the upload is cancelled.
                            
- ?getFileName: null|callback|string, 
                        If callback, takes the default fileName as input and returns the fileName to use (for instance image-shoes.jpg).
                        If string, the string will be used as the fileName.
                        
                        
- ?accept: null|string|callback, whether or not to accept the given file.
                                    If null or not set, the file will be accepted without condition (default).
                                    If string, can be one of:
                                            - image: will be accepted only if it's an image
                                    If callback, takes the file path as entry, and returns a boolean.
- ?uploadAfter: callback, callback to do something with the uploaded file.
                        For instance, you could generate thumbnail(s), delete the original file, and more...




