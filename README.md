Inspect.ps
==========

A recursive inspection library for PostScript, stylised in the vein of Node.js's  colourful `util.inspect()` output:

![Preview of highlighted output](https://raw.githubusercontent.com/Alhadis/Stupid-Post-Tricks/d0f4ce945268d42587fb2e8ec21406ffb2d5a535/assets/%E2%A9%B6.png)


Installation
------------

1.	Download [`inspect.ps`](inspect.ps) to wherever you store your PostScript libraries:
	<pre><code>$ curl <a href="https://git.io/JOsbC">https://git.io/JOsbC</a> &gt; /path/to/ghostscript/lib/inspect.ps</code></pre>

2.	Configure [GhostScript](https://www.ghostscript.com/doc/current/Use.htm#Finding_files) to whitelist the path, if necessary.
	~~~shell
	$ export GS_LIB="/path/to/ghostscript/libs:$GS_LIB"
	~~~

3.	Verify successful installation by running:
	~~~shell
	$ echo '(/path/to/ghostscript/libs) run << /Foo 1 >> ===' \
	| gs -sDEVICE=txtwrite -sOutputFile=- -q -sBATCH -dNOPAUSE -
	~~~


Usage
-----
Use `===` to inspect a single operand:

~~~postscript
userdict ===
~~~

Use `?` to inspect the entire stack à la `pstack`:

~~~postscript
(A) (B) (C) (D) ?
~~~

Neither procedure modifies the stack, so `dup`-ing before inspection is unnecessary.
