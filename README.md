Web Filemanager
===============
Description :
-------------
<pre>
Elfinder is a powerful web based filemanager, built in JS and JQuery. Elfinder features all basic and necessary actions like moving, creating, editing, deleting, renaming etc...
Many free hosting providers doesn't provide online web filemanagement, forcing us to edit/create file/folder in local and upload theme with FTP client.
Actually you can find some solutions on internet :
  - Pydio (Ajaxplorer) (filemanager with editor etc..)
  - ckfinder (filemanager)
  - Codeanywhere (online editor with an integrated ftp client)
  - Codey (online editor with an integrated ftp client)
  
Why elfinder ? Ajaxplorer is much much much better !!

Some filemanager doesn't allow file editing.
Sometimes when you upload files with your ftp client, you encounter some server restrictions, like only popular web formats are allowed.
Or when you try to install a software it says init_set not allowed for security reasons etc....
All these reasons makes installations of ajaxplorer or other powerful filemanager impossible to install.

Online file managers are cool, but sometimes it's slow, or you just can't setup ftp server etc....

So the solution for me is Elfinder. It's free, light, NO UGLY (very important :P), simple to use.
"But ???" Yeah sure, it is not perfect :S
The base editor is really miserable, no synthax highliths, no WYSIWYG editor, it only shows up a little pop up o.O"
WYSIWYG editor integration is complicate, I still doesn't knwo how to ...
The only solution I found, is to integrate codemirror synthax highlighter.

"WYSIWYG editor integration is complicate, I still doesn't knwo how to ..." You kidding me, all these solution on internet, are you blind ?
No no, I'm not, if you read better, it's ALL about integration of elfinder INTO a WYSIWYG editor.


Wish it will be usefull for someone !! o.O"
  </pre>

Used :
-----
- [Elfinder (filemanager)] (http://elfinder.org/)
- [Codemirror (synthax highlighter)] (http://codemirror.net/)

Features
--------
* All operations with files and folders on a remote server (copy, move,
upload, create folder/file, rename, etc.)
* High performance server beckend and light client UI
* Multi-root support
* Local file system, MySQL, FTP volume storage drivers
* Background file upload with Drag & Drop HTML5 support
* List and Icons view
* Kayboard shortcuts
* Standart methods of file/group selection using mouse or keyboard
* Move/Copy files with Drag & Drop
* Archives create/extract (zip, rar, 7z, tar, gzip, bzip2)
* Rich context menu and toolbar
* Quicklook, preview for common file types
* Edit text files **now with synthax highligths, wrapped line, numbered lines**
* Edit images
* "Places" for your favorites
* Calculate directory sizes
* Thumbnails for image files
* Easy to integrate with web editors (elRTE, CKEditor, TinyMCE)
* Flexible configuration of access rights, upload file types, user interface
and other
* Extensibility
* Simple client-server API based on JSON


Requirements
------------

### Client
* Modern browser. elFinder was tested in Firefox 10, Internet Explorer 8+,
Safari 5, Opera 11 and Chrome 15+

### Server
* Any web server
* PHP 5.2+ (for thumbnails - mogrify utility or GD/Imagick module)