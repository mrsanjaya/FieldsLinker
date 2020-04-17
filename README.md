# FieldsLinker

Designed for matching files headers to database fields during the process importing. 
Allows drawing links between elements of 2 lists (headers of the file on the left, column names on the right)
and getting back the result in a js object

Given 2 lists : for instance one from a text import, the second listing the fields a db table
the jquery plugin allows you to draw and save links between the 2 lists

You can link on a one to one basis or on a one to many basis. Fields can be declared as mandatory the result reporting an error in case there are not filled.

Store previous links and headers to automaticaly recognize files
reload links if you need it with the existingLinks property :

example :
"existingLinks": [{ "from": "lastName", "to": "last_name" }, { "from": "firstName", "to": "first_name" }, { "from": "role", "to": "jobTitle" }]


https://philippemarcmeyer.github.io/FieldsLinker/index.html

Also available on https://packagist.org/packages/philippemarcmeyer/fieldslinker ++++

### v0.96 : Removing filter option and alternateview 

### v0.95 : rewritten for multiples instances in mind

### v0.92

Introducing new option : whiteSpace
normal,nowrap,pre,pre-wrap,pre-line,break-spaces default => nowrap

### v0.91

Fix `mobileClickIt` option:

- if set to `true`, will use mobile mode, regardless of touch screen mode.
- fix crash modeB `null` value
- if selected (clicked), use CSS to invert element as visual feedback.
- mobileClickIt option is automatic on touch devices

### v0.90
Canvas calculations fixes and other various fixes.
Filter mode (removed in v 0.96)

### v0.89 

![screen shot](https://raw.githubusercontent.com/PhilippeMarcMeyer/FieldsLinker/master/filedLinker.jpg)

v 0.89 : Corrected a bug that corrupted the links array of objects detected by flartet on github

v 0.88 : New display mode : idea by Naveen nsirangu => show links between two "tables" linked by ids like a join in sql. instead of headers names, objects are provided (removed in v 0.96)

v 0.87 : New option for touch devices {"mobileClickIt":true} : idea by Norman Tomlins => make links more easily on touch devices just by clicking 

v 0.86 : Modifications if Bootstrap is not available : tooltip are basic html titles and the links are horizontally centered

v 0.85 : Mobile friendly (requested by a user)

v 0.80 : I've been cleaning code in order to get something much simpler (nearly the same code than LinksMaker) it allowed me to implement drag and drop to reorder the items in the lists, which is convenient expecially if you've got long lists.
options dropped in this version : autoDetect and byName : no more autodetect and the links are given back by name only not by order.
the link over effect has also been dropped. Important : oneToMany:"on|off" becomes associationMode: "oneToOne|manyToMany"
So you don't have one to many relation + one to one, but instead many to many and one to one relations.

v 0.72 : [Cancelled] New lineStyle : square-ends-dotted : white dots at the beginings and ends of lines on hover

v 0.60 : 
Mandatory fields show a tooltip (mandatoryErrorMessage)
disable/enable : disable/enable everything, the global opacity is set to 0.5

v 0.45 : Mandatory fields. the css is now in his own file.

v 0.41 : the colors don't change when links are deleted and the color of the link while drawing is consistent with the final result

v 0.4 : new option allowing to link one to many

v 0.3 :
FieldsLinker becomes responsive !

v 0.2 :
You can choose beetween an output with positions or names
Colours can be re-defined and lines come in 2 flavours
You may input somme links from a previous session
Auto-detect feature helps you find part of the links (optional)
Optional "Erase Links" button
Works in Chrome, Chromium, Opera, Firefox and IE (9+)

v 0.1  : the lines are drawn while dragging over the canvas and the horizontal middle points of the cells are calculated	
no parameters anymore

Tested on : Chrome, Firefox, Chromium, IE, Opéra : OK for Chrome, Firefox and Opera
todo : horizontal middle points of the cells are wrong on IE 
and on chromium the canvas zone (between the 2 lists) is selected during the dragging process which is not aesthetic.

v0.01 : first commit : todo => parameters should not be necessary cellHeight,List1Width,canvasWidth,List2Width and should be calculated

https://philippemarcmeyer.github.io/FieldsLinker/index.html

<pre>
	var fieldLinks;
		$( document ).ready(function() {
				var input = {
			    "options":{
					"byName" : true,
					"lineStyle":"square-ends",
					"buttonErase":"Erase Links",
					
				},
				"listA":
					{
						"name":"columns in files",
						"list" : [
							"firstName",
							"lastName",
							"phone",
							"email",
							"role",
							"Birthday",
							"Adress",
							"Sales"
						]
					},
				"listB":
					{
						"name":"Fields available",
						"list" : [
							"Id",
							"Company",
							"jobTitle",
							"adress 1",	
							"adress 2",	
							"first_name",
							"last_name",
							"email_adress",
							"Phone number"
						]
					}
					"existingLinks": [{ "from": "lastName", "to": "last_name" }, { "from": "firstName", "to": "first_name" }, { "from": "role", "to": "jobTitle" }]

			};
			
		  	fieldLinks=$("#bonds").fieldsLinker("init",input);
</pre>
