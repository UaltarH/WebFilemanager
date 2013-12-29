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

Elfinder installation :
------------------------
1. Download elfinder [here] (http://elfinder.org/).
2. extract archive to the root of your files or somewhere.
3. go to yoursitepath/elfinder/elfinder.html
4. to set the root path, go in php/connector.php
<pre>
$opts = array(
	// 'debug' => true,
	'roots' => array(
		array(
			'driver'        => 'LocalFileSystem',   // driver for accessing file system (REQUIRED)
			'path'          => '../files/',         // path to files (REQUIRED)
			'URL'           => dirname($_SERVER['PHP_SELF']) . '/../files/', // URL to files (REQUIRED)
			'accessControl' => 'access'             // disable and hide dot starting files (OPTIONAL)
		)
	)
);
</pre>
change path and url.
If you have an error be sure that you put the right path, or try to put absolute path.

Codemirror integration : 
------------------------
1. Download codemirror [here] (http://codemirror.net/).
2. extract files to the root of your files.
3. open elfinder.html, and add this in the head
<pre>
<script src="codemirror/lib/codemirror.js"></script>
<link rel="stylesheet" href="codemirror/lib/codemirror.css">
<link rel="stylesheet" href="codemirror/theme/ambiance.css">
<script src="codemirror/mode/javascript/javascript.js"></script>
</pre>
4. change your init code to this :
<pre>
$().ready(function() {

	var elf = $('#elfinder').elfinder({
		url : 'php/connector.php',

		commandsOptions: {

			edit : {
				// list of allowed mimetypes to edit
				// if empty - any text files can be edited
				mimes : [],

				// you can have a different editor for different mimes
				editors : [{

					mimes : ['text/plain', 'text/html', 'text/javascript', 'text/css', 'text/x-php', 'application/x-httpd-php', 'text/x-markdown'], /*'text/plain', 'text/html', 'text/javascript', 'text/css'*/

					load : function(textarea) {

						this.myCodeMirror = CodeMirror.fromTextArea(textarea, {
							lineNumbers: true,
							theme: "ambiance",
							viewportMargin: Infinity,
							lineWrapping: true
						})
					},

					close : function(textarea, instance) {
						this.myCodeMirror = null;
					},


					save : function(textarea, editor) {
						textarea.value = this.myCodeMirror.getValue();
						this.myCodeMirror = null;
					}

				} ] //editors
			} //edit

		} //commandsoptions

	}).elfinder('instance');

});
</pre>
Codemimrror code changes : 
--------------------------

* to change codemirror theme : <pre>theme: "themename"</pre> and include theme file in the head
* line wrapping : <pre>lineWrapping: true</pre>
* auto-resize in the css file: 
<pre>.CodeMirror {
  border: 1px solid #eee;
  height: auto;
}
.CodeMirror-scroll {
  overflow-y: hidden;
  overflow-x: auto;
}</pre>
in elfinder.html: 
<pre>viewportMargin: Infinity</pre>

Elfinder code changes :
-----------------------
1. to change elfinder's height, go in js/elfinder.min.js, find search "dateFormat" and change height value, here I changed to 500 (in px)
<pre>dateFormat:"",fancyDateFormat:"",width:"auto",height:500,resizable:!</pre>
2. to change editor's width search "dialogWidth" and change value, here I changed value to 1000 (in px)
<pre>k={title:e.name,width:b.options.dialogWidth||1000,buttons:{}</pre>