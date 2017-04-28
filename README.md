Upload profiles
==================
2017-04-28



A system to handle file uploads in a modular architecture.



[![upload-profile.jpg](https://s19.postimg.org/jr53wxnfn/upload-profile.jpg)](https://postimg.org/image/iouxee4m7/)





The main idea is that when an upload is done, only an identifier is transmitted, so that the upload configuration data (where to put the uploaded file,
what's the max size, ...) is not corrupted.


To achieve that, a collection of upload profiles is created in a configuration file (**upload-profile.conf.php** in the schema).

This profile collection is used both by the javascript helper and the server side script, as to ensure consistency for handling the upload.










