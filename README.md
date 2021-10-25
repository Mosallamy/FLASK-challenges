<div align="center">
	<img src="https://github.com/Mosallamy/FLASK-challenges/raw/main/Header.png">
</div>

## FLASK Challenges
This repo is a collection for the issues I faced when I started learning Flask.

It's meant to help beginners avoid the HELL of trying to solve problems at the start of learning a new framework.

Topics covered:
 - [Database connection](#Database-connections)
	 - SQLAlchemy
		 - Installation
		 - db.create_all()
		 - Data not updated
	 - MySQL
		 - Installation
 - [PDF generation](#PDF-generation)
	 - WKHTMLTOPDF
		 - Installation
		 - Deployment
	 - PdfKit
		 - not rendering image
 - [Runtime errors](#Runtime-errors)
	 - PermissionError: [Errno 13] Permission denied
	 - OSError: [Errno 48] Address already in use
 - [Jinja](#Jinja)
	 - [Global variables](#Global-variables)

## Database connections
##  PDF generation
## Runtime errors
## Jinja
### Global variables
Unfortiannely Jinja does not support global variables. The below example shows the issue:
```jinja2
{% set sum = 0 %}
{{ sum }} {# sum = 0 #}

{% for i in range(1,6) %}  
	{% set sum = sum +  i %}  
{% endfor %}

{{ sum }} {# sum = 0 instead of 15 #}
```
**There are two ways around this limitation:**
 1. **Using namespace (Added in version 2.10)**
	 1.1 Example 1: summing numbers in a loop 
	```jinja2
	{% set global_var = namespace(sum=0) %}  
	{{ global_var.sum }} {# sum = 0 #}

	{% for i in range(1,6) %}  
	    {% set global_var.sum = i + global_var.sum %}  
	{% endfor %}

	{{ global_var.sum }} {# sum = 15 #}
	```
	 1.2 Example 2: global flag 
	```jinja2
	{% set global_var = namespace(flag=false) %}  
	  
	{% for i in range(1,6) %}  
	    {% if i == 4 %}  
	        {% set global_var.flag=true %}  
	    {% endif %}  
	{% endfor %}  
	  
	{% if global_var.flag %} 4 was found! {% endif %} {# Condition is true #}
	```
> Added in version 2.10
 2. **Using global list**
```jinja2
{% set global_list = [] %}  
{{ global_list }} {# global_list = [] #}  

{% for i in range(1,6) %}  
    {% if global_list.append(i) %}{% endif %}  
{% endfor %}  
  
{{ global_list }} {# global_list = [1, 2, 3, 4, 5] #}
```
## Resources you will benifit from
 - YouTube channels
	 -  [Corey Schafer](https://www.youtube.com/c/Coreyms)
	 - [Pretty Printed](https://www.youtube.com/c/PrettyPrintedTutorials)
 - Articles
	 - [Full Stack Python](https://www.fullstackpython.com)

## License

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
