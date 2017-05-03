title: How to use python absolute import in package?
category: Python
date: 2017-04-12
tags:
- Python
- Absolute-Import
lede: "When you work on a complicated python project, there are many custom packages. In order to manage these packages and avoid shadowing stardand libary, we intend to use absolute import. But there are something you should be careful when you use it."
featured: true
---

When you work on a complicated python project, there are many custom packages. In order to manage these packages and avoid shadowing stardand libary, we intend to use absolute import. But there are something you should be careful when you use it.

<!-- more -->

# Python absolute import

## Absolute import

I had been confused for quite a long time about how python absolute import works.

Why should we use absolute import? The [rationale](https://www.python.org/dev/peps/pep-0328/#rationale-for-absolute-imports) maybe:
{% blockquote %}
In Python 2.4 and earlier, if you're reading a module located inside a package, it is not clear whether 

	import foo
refers to a top-level module or to another module inside the package. As Python's library expands, more and more existing package internal modules suddenly shadow standard library modules by accident. It's a particularly difficult problem inside packages because there's no way to specify which module is meant. To resolve the ambiguity, it is proposed that foo will always be a module or package reachable from sys.path . This is called an absolute import.
{% endblockquote %}

As absolute import includes the namesapce for the imported package, users can also get a better understading for what this package does. And it's always a good habit to avoid name comflicts in a complicated project.

## Use in custom package

Okay, so how to use it? Is there any "hello world" demo I can try it out? I found a changelog([more details](https://docs.python.org/2.5/whatsnew/pep-328.html)) about absolute import when python2.5 distributed, alongside with a easy example:

	pkg/
	pkg/__init__.py
	pkg/main.py
	pkg/string.py

`main.py` is
 
``` python
from __future__ import absolute_import
from pkg import string
print(string)
string.sayHello()
```
Note that we can use `from __future__ import absolute_import` to obtain absolute import if you are running python2.* .

`string.py` is

``` python
def sayHello():
    print('Hello World!')
```
and leave `__init__.py` empty.

When you run `python main.py` in terminal or in an IDE, it would come across an ERROR, `ImportError: No module named pkg`. This seems weird, we do exactly as the example says, why doesn't it work?

There is something not clear with the changelog, or you should have some extra knowledge about [python import system](https://docs.python.org/3/reference/import.html). Absolute import actually finds top-level module or package reachable from `sys.path`. So we ran across `ImportError` because our custom package path not in the `sys.path`. 

In order to fix this, we can either `cd` to package folder and run as

	python -m pkg.main
	
or add our custom package to PYTHONPATH. In a big project, I suggest add our package path in `.bashrc`(`.bash_profile` in Mac) eg:

	export PYTHONPATH="your/project/package/:$PYTHONPATH"

or write a script every time you want to use this package, then source that script.

## Additional issue

In addition, there is also something not so right with the changelog as follows:
{% blockquote %}
In Python 2.5, you can switch import's behaviour to absolute imports using a from __future__ import absolute_import directive. This absolute-import behaviour will become the default in a future version (probably Python 2.7). Once absolute imports are the default, import string will always find the standard library's version.
{% endblockquote %}

`import string` would point to the `string.py` file in current foler, and would not import string from standard library. Because absolute import **finds top-level module or package reachable from `sys.path`, and current folder path always the first element in the `sys.path`.** More details you can find in [this stackoverflow link](http://stackoverflow.com/questions/33743880/what-does-from-future-import-absolute-import-actually-do).
