
*** Parameters: ***
require 'maruku/ext/math'; {}
*** Markdown input: ***
Here are some formulas:

*	$\alpha$
*	$x^{n}+y^{n} \neq z^{n}$

That's it, nothing else is supported.

*** Output of inspect ***
md_el(:document,[
	md_par(["Here are some formulas:"]),
	md_el(:ul,[
		md_el(:li_span,[md_el(:inline_math,[],{:math=>"\\alpha"},[])],{:want_my_paragraph=>false},[]),
		md_el(:li_span,[md_el(:inline_math,[],{:math=>"x^{n}+y^{n} \\neq z^{n}"},[])],{:want_my_paragraph=>false},[])
	],{},[]),
	md_par(["That", md_entity("rsquo"), "s it, nothing else is supported."])
],{},[])
*** Output of to_html ***
<p>Here are some formulas:</p>

<ul>
<li><span class='maruku-inline'><code class='maruku-mathml'>\alpha</code></span></li>

<li><span class='maruku-inline'><code class='maruku-mathml'>x^{n}+y^{n} \neq z^{n}</code></span></li>
</ul>

<p>That&#8217;s it, nothing else is supported.</p>
*** Output of to_latex ***
Here are some formulas:

\begin{itemize}%
\item $\alpha$
\item $x^{n}+y^{n} \neq z^{n}$

\end{itemize}
That'{}s it, nothing else is supported.
*** Output of to_md ***
Here are some formulas:

--
That s it, nothing else is supported.
*** Output of to_s ***
Here are some formulas:Thats it, nothing else is supported.
*** EOF ***



	OK!



*** Output of Markdown.pl ***
<p>Here are some formulas:</p>

<ul>
<li>$\alpha$</li>
<li>$x^{n}+y^{n} \neq z^{n}$</li>
</ul>

<p>That's it, nothing else is supported.</p>

*** Output of Markdown.pl (parsed) ***
Error: #<NoMethodError: private method `write_children' called for <div> ... </>:REXML::Element>
