---


---

<p>Got it — here’s your <strong>6-minute revision note</strong> (focused + fixing your weak spots).</p>
<hr>
<h1 id="🚀-java-method-reference-—-revision-notes">🚀 JAVA METHOD REFERENCE — REVISION NOTES</h1>
<h2 id="🔹-1.-what-is-method-reference">🔹 1. What is Method Reference?</h2>
<p>Shortcut of lambda. written wiht <code>::</code>before the method name.</p>
<pre class=" language-java"><code class="prism  language-java">x <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span>

</code></pre>
<p>➡️</p>
<pre class=" language-java"><code class="prism  language-java">System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println

</code></pre>
<p>👉 Use when <strong>lambda only calls a method</strong>.</p>
<hr>
<h2 id="🔹-2.-golden-rule-you-missed-this-⚠️">🔹 2. GOLDEN RULE (YOU MISSED THIS ⚠️)</h2>
<p>👉 <strong>Signature must match Functional Interface</strong></p>
<p>Always check:</p>
<ul>
<li>
<p>Input parameters</p>
</li>
<li>
<p>Return type</p>
</li>
</ul>
<hr>
<h2 id="🔹-3.-functional-interfaces-mapping-very-important">🔹 3. Functional Interfaces Mapping (VERY IMPORTANT)</h2>

<table>
<thead>
<tr>
<th>Interface</th>
<th>Meaning</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>T → R</code></td>
<td><code>String → int</code></td>
<td><code>Fucntion&lt;String, Integer&gt;</code></td>
</tr>
<tr>
<td><code>T → void</code></td>
<td>print</td>
<td><code>Consumer&lt;String&gt;</code></td>
</tr>
<tr>
<td><code>()-&gt;T</code></td>
<td><code>new Object</code></td>
<td><code>Supplier&lt;ClassName&gt;</code></td>
</tr>
<tr>
<td><code>T-&gt;boolean</code></td>
<td>filter</td>
<td><code>Predicate&lt;T&gt;</code></td>
</tr>
<tr>
<td>(T,U) → R</td>
<td>compare</td>
<td><code>BiFunction&lt;T,U,&gt;</code></td>
</tr>
</tbody>
</table><hr>
<h2 id="🔥-4.-types-of-method-references">🔥 4. Types of Method References</h2>
<h2 id="static-method">1. Static Method</h2>
<pre class=" language-java"><code class="prism  language-java">Class<span class="token operator">:</span><span class="token operator">:</span>staticMethod

</code></pre>
<p>✔ Example:</p>
<pre class=" language-java"><code class="prism  language-java">Function<span class="token operator">&lt;</span>String<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> Integer<span class="token operator">:</span><span class="token operator">:</span>parseInt<span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="object-method-specific-object">2. Object Method (Specific Object)</h2>
<pre class=" language-java"><code class="prism  language-java">obj<span class="token operator">:</span><span class="token operator">:</span>method

</code></pre>
<p>✔ Example:</p>
<pre class=" language-java"><code class="prism  language-java">Printer p <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Printer</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
Consumer<span class="token operator">&lt;</span>String<span class="token operator">&gt;</span> c <span class="token operator">=</span> p<span class="token operator">:</span><span class="token operator">:</span>print<span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="arbitrary-object-you-were-confused-here-⚠️">3. Arbitrary Object (YOU WERE CONFUSED HERE ⚠️)</h2>
<pre class=" language-java"><code class="prism  language-java">Class<span class="token operator">:</span><span class="token operator">:</span>instanceMethod

</code></pre>
<p>✔ Example:</p>
<pre class=" language-java"><code class="prism  language-java">BiPredicate<span class="token operator">&lt;</span>String<span class="token punctuation">,</span> String<span class="token operator">&gt;</span> p <span class="token operator">=</span> String<span class="token operator">:</span><span class="token operator">:</span>equals<span class="token punctuation">;</span>

</code></pre>
<p>👉 Internally:</p>
<pre class=" language-java"><code class="prism  language-java"><span class="token punctuation">(</span>s1<span class="token punctuation">,</span> s2<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> s1<span class="token punctuation">.</span><span class="token function">equals</span><span class="token punctuation">(</span>s2<span class="token punctuation">)</span>

</code></pre>
<p>⚠️ FIRST PARAM becomes OBJECT</p>
<hr>
<h3 id="constructor-reference">4. Constructor Reference</h3>
<pre class=" language-java"><code class="prism  language-java">Class<span class="token operator">:</span><span class="token operator">:</span><span class="token keyword">new</span>

</code></pre>
<p>✔ Example:</p>
<pre class=" language-java"><code class="prism  language-java">Supplier<span class="token operator">&lt;</span>ArrayList<span class="token operator">&lt;</span>String<span class="token operator">&gt;&gt;</span> s <span class="token operator">=</span> ArrayList<span class="token operator">:</span><span class="token operator">:</span><span class="token keyword">new</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="⚠️-your-mistakes-fixed">⚠️ YOUR MISTAKES FIXED</h2>
<h2 id="❌-mistake-1-wrong-interface">❌ Mistake 1: Wrong Interface</h2>
<pre class=" language-java"><code class="prism  language-java">Consumer<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> <span class="token operator">=</span> Integer<span class="token operator">:</span><span class="token operator">:</span>parseInt

</code></pre>
<p>👉 parseInt = (String → int)</p>
<p>✅ Correct:</p>
<pre class=" language-java"><code class="prism  language-java">Function<span class="token operator">&lt;</span>String<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> Integer<span class="token operator">:</span><span class="token operator">:</span>parseInt<span class="token punctuation">;</span>

</code></pre>
<hr>
<h3 id="❌-mistake-2-return-type-mismatch">❌ Mistake 2: Return Type Mismatch</h3>
<pre class=" language-java"><code class="prism  language-java">Predicate<span class="token operator">&lt;</span>Boolean<span class="token operator">&gt;</span> <span class="token operator">=</span> String<span class="token operator">:</span><span class="token operator">:</span>compareTo

</code></pre>
<p>👉 compareTo returns int, not boolean</p>
<p>✅ Correct:</p>
<pre class=" language-java"><code class="prism  language-java">BiFunction<span class="token operator">&lt;</span>String<span class="token punctuation">,</span> String<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> String<span class="token operator">:</span><span class="token operator">:</span>compareTo<span class="token punctuation">;</span>

</code></pre>
<hr>
<h3 id="❌-mistake-3-constructor--consumer-confusion">❌ Mistake 3: Constructor + Consumer Confusion</h3>
<pre class=" language-java"><code class="prism  language-java">Consumer<span class="token operator">&lt;</span>HashMap<span class="token operator">&gt;</span> <span class="token operator">=</span> HashMap<span class="token operator">:</span><span class="token operator">:</span><span class="token keyword">new</span>

</code></pre>
<p>👉 Constructor returns object → not void</p>
<p>✅ Correct:</p>
<pre class=" language-java"><code class="prism  language-java">Supplier<span class="token operator">&lt;</span>HashMap<span class="token operator">&lt;</span>String<span class="token punctuation">,</span> Integer<span class="token operator">&gt;&gt;</span> s <span class="token operator">=</span> HashMap<span class="token operator">:</span><span class="token operator">:</span><span class="token keyword">new</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h3 id="🧠-super-important-patterns">🧠 SUPER IMPORTANT PATTERNS</h3>
<h3 id="pattern-1">Pattern 1</h3>
<pre class=" language-java"><code class="prism  language-java">x <span class="token operator">-</span><span class="token operator">&gt;</span> Class<span class="token punctuation">.</span><span class="token function">method</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span>

</code></pre>
<p>➡️ <code>Class::method</code></p>
<hr>
<h3 id="pattern-2">Pattern 2</h3>
<pre class=" language-java"><code class="prism  language-java"><span class="token punctuation">(</span>x<span class="token punctuation">,</span> y<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> x<span class="token punctuation">.</span><span class="token function">method</span><span class="token punctuation">(</span>y<span class="token punctuation">)</span>

</code></pre>
<p>➡️ <code>Class::method</code></p>
<hr>
<h3 id="pattern-3">Pattern 3</h3>
<pre class=" language-java"><code class="prism  language-java"><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token keyword">new</span> <span class="token class-name">Class</span><span class="token punctuation">(</span><span class="token punctuation">)</span>

</code></pre>
<p>➡️ <code>Class::new</code></p>
<hr>
<h3 id="⚡-real-use-most-common">⚡ REAL USE (MOST COMMON)</h3>
<h2 id="streams">Streams</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>String<span class="token operator">:</span><span class="token operator">:</span>toUpperCase<span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="sorting">Sorting</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">sort</span><span class="token punctuation">(</span>String<span class="token operator">:</span><span class="token operator">:</span>compareTo<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="filtering">Filtering</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>String<span class="token operator">:</span><span class="token operator">:</span>isEmpty<span class="token punctuation">)</span>

</code></pre>
<hr>
<h1 id="⚠️-when-not-to-use">⚠️ WHEN NOT TO USE</h1>
<p>If logic &gt; 1 step:</p>
<pre class=" language-java"><code class="prism  language-java">x <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
   <span class="token keyword">int</span> y <span class="token operator">=</span> x <span class="token operator">*</span> <span class="token number">2</span><span class="token punctuation">;</span>
   <span class="token keyword">return</span> y <span class="token operator">+</span> <span class="token number">5</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

</code></pre>
<p>❌ No method reference possible</p>
<hr>
<h1 id="🧠-final-memory-hook">🧠 FINAL MEMORY HOOK</h1>
<p>👉 Ask:<br>
<strong>“What goes in? What comes out?”</strong></p>
<p>Then match:</p>
<ul>
<li>
<p>Input → parameters</p>
</li>
<li>
<p>Output → return type</p>
</li>
</ul>
<hr>
<h1 id="⚡-30-second-cheat-sheet">⚡ 30-SECOND CHEAT SHEET</h1>

<table>
<thead>
<tr>
<th>Lambda</th>
<th>Method Ref</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>x -&gt; foo(x)</code></td>
<td><code>Class::foo</code></td>
</tr>
<tr>
<td><code>(x,y) -&gt; x.foo(y)</code></td>
<td><code>Class::foo</code></td>
</tr>
<tr>
<td><code>() -&gt; new A()</code></td>
<td><code>A::new</code></td>
</tr>
</tbody>
</table><hr>
<h1 id="🎯-your-weak-areas-fix-these">🎯 YOUR WEAK AREAS (FIX THESE)</h1>
<ol>
<li>
<p>❌ Not checking return type</p>
</li>
<li>
<p>❌ Confusing Consumer vs Function</p>
</li>
<li>
<p>❌ Not understanding <code>(x,y)-&gt;x.method(y)</code> pattern</p>
</li>
<li>
<p>❌ Constructor ≠ Consumer</p>
</li>
</ol>
<hr>
<h1 id="🚀-iterator-vs-listiterator-—-quick-notes">🚀 ITERATOR vs LISTITERATOR — QUICK NOTES</h1>
<h2 id="🔹-core-difference">🔹 Core Difference</h2>
<pre><code>	Interfaces used to traverse collcetions.
</code></pre>
<p><strong><code>ListIterator</code></strong> interface <strong>extends</strong> the <strong><code>Iterator</code></strong> interface in Java</p>
<ul>
<li><strong>Iterator</strong> → basic traversal (forward only)</li>
<li><strong>ListIterator</strong> → advanced traversal (forward + backward + modify)</li>
</ul>

<table>
<thead>
<tr>
<th>Feature</th>
<th>Iterator</th>
<th>ListIterator</th>
</tr>
</thead>
<tbody>
<tr>
<td>Works On</td>
<td><code>All collections</code></td>
<td>Only <code>List</code></td>
</tr>
<tr>
<td>Direction</td>
<td><code>Forward only</code></td>
<td><code>Forward + Backward</code></td>
</tr>
<tr>
<td>Data Modification power</td>
<td><code>remove</code></td>
<td><code>add</code>,<code>remove</code>,<code>set</code></td>
</tr>
</tbody>
</table><h2 id="iterator-different-methods">Iterator Different Methods</h2>
<p>`</p>
<pre><code>    List&lt;Integer&gt; list = new ArrayList&lt;&gt;(Arrays.asList(10, 20, 30, 40));
    Iterator&lt;Integer&gt; it = list.iterator();

    while(it.hasNext()) {                 // check next
        int val = it.next();              // move + get

        if(val == 20) {
            it.remove();                 // remove safely
        }

        System.out.println(val);
    }

    System.out.println("Final List: " + list);
}
</code></pre>
<p>}`</p>
<h2 id="listiterator-different-methods">ListIterator Different Methods</h2>
<pre><code>    List&lt;String&gt; list = new ArrayList&lt;&gt;(Arrays.asList("A", "B", "C"));
	ListIterator&lt;String&gt; it = list.listIterator();

    // Forward traversal
    while(it.hasNext()) {
        String val = it.next();

        if(val.equals("A")) {
            it.set("AA");      // update
        }

        if(val.equals("B")) {
            it.add("BB");      // add after B
        }
    }

    System.out.println("After forward: " + list);

    // Backward traversal
    while(it.hasPrevious()) {
        String val = it.previous();

        if(val.equals("C")) {
            it.remove();       // remove safely
        }

        System.out.println("Backward: " + val);
    }

    System.out.println("Final List: " + list);
}
</code></pre>
<hr>
<p>Here’s your <strong>5–6 min revision note — Lambda Expressions + Functional Interfaces</strong> (same style as your previous notes, focused + fixes your weak spots).</p>
<hr>
<h1 id="🚀-lambda-expressions-—-revision-notes">🚀 LAMBDA EXPRESSIONS — REVISION NOTES</h1>
<h2 id="🔹-1.-what-is-lambda">🔹 1. What is Lambda?</h2>
<p>👉 Shortcut to implement a functional interface using an <strong>anonymous function</strong></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token punctuation">(</span>a<span class="token punctuation">,</span> b<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> a <span class="token operator">+</span> b

</code></pre>
<hr>
<h2 id="🧠-professional-definition">🧠 Professional Definition</h2>
<p>👉<br>
“A lambda expression is a concise representation of an anonymous function used to implement a functional interface.”</p>
<hr>
<h1 id="🔥-2.-functional-interface-very-important">🔥 2. Functional Interface (VERY IMPORTANT)</h1>
<p>👉 Interface with <strong>exactly ONE abstract method</strong></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token annotation punctuation">@FunctionalInterface</span>
<span class="token keyword">interface</span> <span class="token class-name">MyFunc</span> <span class="token punctuation">{</span>
    <span class="token keyword">int</span> <span class="token function">apply</span><span class="token punctuation">(</span><span class="token keyword">int</span> a<span class="token punctuation">,</span> <span class="token keyword">int</span> b<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

</code></pre>
<p>✔ Lambda implements it:</p>
<pre class=" language-java"><code class="prism  language-java">MyFunc f <span class="token operator">=</span> <span class="token punctuation">(</span>a<span class="token punctuation">,</span> b<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> a <span class="token operator">+</span> b<span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚡-3.-lambda-syntax-variations">⚡ 3. Lambda Syntax Variations</h1>
<hr>
<h2 id="✅-1.-single-parameter">✅ 1. Single Parameter</h2>
<pre class=" language-java"><code class="prism  language-java">Consumer<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> c <span class="token operator">=</span> x <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<p>✔ No brackets needed</p>
<hr>
<h2 id="✅-2.-multiple-parameters">✅ 2. Multiple Parameters</h2>
<pre class=" language-java"><code class="prism  language-java">BiFunction<span class="token operator">&lt;</span>Integer<span class="token punctuation">,</span> Integer<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> <span class="token punctuation">(</span>a<span class="token punctuation">,</span> b<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> a <span class="token operator">+</span> b<span class="token punctuation">;</span>

</code></pre>
<p>✔ Brackets mandatory</p>
<hr>
<h2 id="✅-3.-with-return-type">✅ 3. With Return Type</h2>
<pre class=" language-java"><code class="prism  language-java">Function<span class="token operator">&lt;</span>Integer<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">*</span> x<span class="token punctuation">;</span>

</code></pre>
<p>✔ No <code>return</code> needed (single expression)</p>
<hr>
<h2 id="⚠️-4.-multiple-statements-important">⚠️ 4. Multiple Statements (IMPORTANT)</h2>
<pre class=" language-java"><code class="prism  language-java">Function<span class="token operator">&lt;</span>Integer<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> f <span class="token operator">=</span> x <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
    <span class="token keyword">int</span> y <span class="token operator">=</span> x <span class="token operator">*</span> <span class="token number">2</span><span class="token punctuation">;</span>
    <span class="token keyword">return</span> y <span class="token operator">+</span> <span class="token number">5</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>

</code></pre>
<p>❗ Must use <code>{}</code> and <code>return</code></p>
<hr>
<h2 id="✅-5.-without-return-void">✅ 5. Without Return (void)</h2>
<pre class=" language-java"><code class="prism  language-java">Consumer<span class="token operator">&lt;</span>String<span class="token operator">&gt;</span> c <span class="token operator">=</span> s <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>s<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚠️-common-mistake-you-had-this-type">⚠️ COMMON MISTAKE (YOU HAD THIS TYPE)</h1>
<p>❌</p>
<pre class=" language-java"><code class="prism  language-java">x <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
   <span class="token keyword">int</span> y <span class="token operator">=</span> x <span class="token operator">*</span> <span class="token number">2</span><span class="token punctuation">;</span>
   y <span class="token operator">+</span> <span class="token number">5</span><span class="token punctuation">;</span>   <span class="token comment">// ❌ missing return</span>
<span class="token punctuation">}</span>

</code></pre>
<hr>
<hr>
<h1 id="🧠-golden-rule">🧠 GOLDEN RULE</h1>
<p>👉 Match:<br>
<strong>Input → parameters</strong><br>
<strong>Output → return type</strong></p>
<hr>
<h1 id="🔥-5.-lambdas-with-collections-most-important">🔥 5. Lambdas with Collections (MOST IMPORTANT)</h1>
<hr>
<h2 id="foreach">forEach()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>x<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<p>✔ Better:</p>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="filter">filter()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">&gt;</span> <span class="token number">10</span><span class="token punctuation">)</span>

</code></pre>
<hr>
<h2 id="map">map()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">*</span> x<span class="token punctuation">)</span>

</code></pre>
<hr>
<h1 id="⚡-code-1-core-lambda-usage">⚡ CODE 1: Core Lambda Usage</h1>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>function<span class="token punctuation">.</span>*<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Main</span> <span class="token punctuation">{</span>
    <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>

        <span class="token comment">// Function (return type)</span>
        Function<span class="token operator">&lt;</span>Integer<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> square <span class="token operator">=</span> x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">*</span> x<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>square<span class="token punctuation">.</span><span class="token function">apply</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

        <span class="token comment">// Consumer (no return)</span>
        Consumer<span class="token operator">&lt;</span>String<span class="token operator">&gt;</span> print <span class="token operator">=</span> s <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>s<span class="token punctuation">)</span><span class="token punctuation">;</span>
        print<span class="token punctuation">.</span><span class="token function">accept</span><span class="token punctuation">(</span><span class="token string">"Hello"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

        <span class="token comment">// Predicate (boolean)</span>
        Predicate<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> isEven <span class="token operator">=</span> x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>isEven<span class="token punctuation">.</span><span class="token function">test</span><span class="token punctuation">(</span><span class="token number">4</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

        <span class="token comment">// Supplier (no input)</span>
        Supplier<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> random <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token number">100</span><span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>random<span class="token punctuation">.</span><span class="token function">get</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

        <span class="token comment">// BiFunction (two inputs)</span>
        BiFunction<span class="token operator">&lt;</span>Integer<span class="token punctuation">,</span> Integer<span class="token punctuation">,</span> Integer<span class="token operator">&gt;</span> sum <span class="token operator">=</span> <span class="token punctuation">(</span>a<span class="token punctuation">,</span> b<span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> a <span class="token operator">+</span> b<span class="token punctuation">;</span>
        System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>sum<span class="token punctuation">.</span><span class="token function">apply</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

</code></pre>
<hr>
<h1 id="⚡-code-2-lambdas-with-collections-most-important">⚡ CODE 2: Lambdas with Collections (MOST IMPORTANT)</h1>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>*<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Main</span> <span class="token punctuation">{</span>
    <span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">void</span> <span class="token function">main</span><span class="token punctuation">(</span>String<span class="token punctuation">[</span><span class="token punctuation">]</span> args<span class="token punctuation">)</span> <span class="token punctuation">{</span>

        List<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> nums <span class="token operator">=</span> Arrays<span class="token punctuation">.</span><span class="token function">asList</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

        nums<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
            <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>n <span class="token operator">-</span><span class="token operator">&gt;</span> n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span>      <span class="token comment">// Predicate</span>
            <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>n <span class="token operator">-</span><span class="token operator">&gt;</span> n <span class="token operator">*</span> n<span class="token punctuation">)</span>              <span class="token comment">// Function</span>
            <span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>n <span class="token operator">-</span><span class="token operator">&gt;</span> System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>n<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// Consumer</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>

</code></pre>
<hr>
<h1 id="⚠️-your-weak-areas-focus-here">⚠️ YOUR WEAK AREAS (FOCUS HERE)</h1>
<ol>
<li>
<p>❌ Forgetting <code>return</code> in multi-line lambda</p>
</li>
<li>
<p>❌ Choosing wrong functional interface</p>
</li>
<li>
<p>❌ Not recognizing when to use <code>Consumer vs Function</code></p>
</li>
<li>
<p>❌ Not converting simple lambda → method reference</p>
</li>
</ol>
<hr>
<h1 id="🧠-memory-shortcut">🧠 MEMORY SHORTCUT</h1>
<p>👉 Ask:</p>
<ul>
<li>
<p>Returns value? → <code>Function</code></p>
</li>
<li>
<p>Only action? → <code>Consumer</code></p>
</li>
<li>
<p>Boolean? → <code>Predicate</code></p>
</li>
<li>
<p>No input? → <code>Supplier</code></p>
</li>
</ul>
<hr>
<h2 id="⚡variety-of-lambda-function">⚡VAriety of Lambda function</h2>

<table>
<thead>
<tr>
<th>Case</th>
<th>Lambda</th>
</tr>
</thead>
<tbody>
<tr>
<td>Single param</td>
<td><code>x -&gt; x*2</code></td>
</tr>
<tr>
<td>Two param</td>
<td><code>(a,b) -&gt; a+b</code></td>
</tr>
<tr>
<td>ulti-line</td>
<td><code>{ return ... }</code></td>
</tr>
<tr>
<td>Void</td>
<td><code>x -&gt; print(x)</code></td>
</tr>
</tbody>
</table><hr>
<h2 id="what-are-generics-in-java">What are Generics in Java?</h2>
<p>Generics mean  <strong>parameterized types</strong>. They allow you to define a class, interface, or method with placeholders (<code>&lt;T&gt;</code>,  <code>&lt;E&gt;</code>, etc.) for the data types they will use. The specific type is defined only when the class is instantiated or the method is called.</p>
<h3 id="what-is-non-generic-in-java">What is Non-Generic in Java?</h3>
<p>Before Generics, collections and classes were designed to work with the  <code>Object</code>  class, which is the superclass of all Java classes. This approach is known as using “raw types”</p>
<pre><code>List names = new ArrayList(); // Raw Type(Non Generic)
names.add("John");
names.add(10); // Compiler allows this, but it's a bug!
String name = (String) names.get(1); // Runtime Exception: ClassCastException

List&lt;String&gt; names = new ArrayList&lt;String&gt;(); // Type-safe
names.add("John");
// names.add(10); // Compile-time Error!
String name = names.get(0); // No casting needed
</code></pre>
<hr>
<h2 id="🌍-locale">🌍 Locale</h2>
<h2 id="🔹-what-is-locale">🔹 What is Locale?</h2>
<p>👉 Represents <strong>language + region</strong></p>
<pre><code>import java.util.*;

Locale l1 = new Locale("en", "US");
Locale l2 = Locale.FRANCE;

System.out.println(l1.getDisplayLanguage());
System.out.println(l2.getDisplayCountry());
</code></pre>
<hr>
<h2 id="🔥-use-cases">🔥 Use Cases</h2>
<h3 id="currency-formatting">1. Currency Formatting</h3>
<pre><code>import java.text.NumberFormat;

NumberFormat nf = NumberFormat.getCurrencyInstance(Locale.US);
System.out.println(nf.format(1234.5));
</code></pre>
<h3 id="date-formatting-using-locale">2.Date formatting using Locale</h3>
<pre><code>import java.time.*;
import java.time.format.*;

DateTimeFormatter f =
    DateTimeFormatter.ofPattern("dd MMM yyyy", Locale.FRANCE);

System.out.println(LocalDate.now().format(f));
</code></pre>
<hr>
<p>Here’s your <strong>10-minute high-impact revision sheet — Java Date &amp; Time (<code>java.time</code>) methods</strong>, organized <strong>by use-case</strong> (this is how interviewers expect you to think).</p>
<hr>
<h1 id="🚀-1.-create-date--time">🚀 1. CREATE DATE / TIME</h1>
<h2 id="🔹-use-case-create-current-or-specific-datetime">🔹 Use case: Create current or specific date/time</h2>
<pre class=" language-java"><code class="prism  language-java">LocalDate<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
LocalTime<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
LocalDateTime<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

LocalDate<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token number">2025</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
LocalTime<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
LocalDateTime<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token number">2025</span><span class="token punctuation">,</span> <span class="token number">4</span><span class="token punctuation">,</span> <span class="token number">20</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">,</span> <span class="token number">30</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<p>👉 Parse from string:</p>
<pre class=" language-java"><code class="prism  language-java">LocalDate<span class="token punctuation">.</span><span class="token function">parse</span><span class="token punctuation">(</span><span class="token string">"2025-04-20"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="📅-2.-add--subtract-date--time">📅 2. ADD / SUBTRACT DATE &amp; TIME</h1>
<h2 id="🔹-use-case-scheduling-deadlines">🔹 Use case: Scheduling, deadlines</h2>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">plusDays</span><span class="token punctuation">(</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">minusMonths</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

time<span class="token punctuation">.</span><span class="token function">plusHours</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
time<span class="token punctuation">.</span><span class="token function">minusMinutes</span><span class="token punctuation">(</span><span class="token number">15</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

dateTime<span class="token punctuation">.</span><span class="token function">plusDays</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">plusHours</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<p>👉 Generic:</p>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">plus</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span> ChronoUnit<span class="token punctuation">.</span>WEEKS<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔍-3.-compare-dates">🔍 3. COMPARE DATES</h1>
<h2 id="🔹-use-case-validation-sorting">🔹 Use case: validation, sorting</h2>
<pre class=" language-java"><code class="prism  language-java">date1<span class="token punctuation">.</span><span class="token function">isBefore</span><span class="token punctuation">(</span>date2<span class="token punctuation">)</span><span class="token punctuation">;</span>
date1<span class="token punctuation">.</span><span class="token function">isAfter</span><span class="token punctuation">(</span>date2<span class="token punctuation">)</span><span class="token punctuation">;</span>
date1<span class="token punctuation">.</span><span class="token function">isEqual</span><span class="token punctuation">(</span>date2<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="📊-4.-get-details-from-date">📊 4. GET DETAILS FROM DATE</h1>
<h2 id="🔹-use-case-reporting">🔹 Use case: reporting</h2>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">getDayOfWeek</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">getMonth</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">getYear</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">getDayOfMonth</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔁-5.-iterate-date-range">🔁 5. ITERATE DATE RANGE</h1>
<h2 id="🔹-use-case-reports-bookings">🔹 Use case: reports, bookings</h2>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">while</span> <span class="token punctuation">(</span><span class="token operator">!</span>start<span class="token punctuation">.</span><span class="token function">isAfter</span><span class="token punctuation">(</span>end<span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>start<span class="token punctuation">)</span><span class="token punctuation">;</span>
    start <span class="token operator">=</span> start<span class="token punctuation">.</span><span class="token function">plusDays</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

</code></pre>
<hr>
<h1 id="🎨-6.-format-datetime-very-important">🎨 6. FORMAT DATE/TIME (VERY IMPORTANT)</h1>
<h2 id="🔹-use-case-display">🔹 Use case: display</h2>
<pre class=" language-java"><code class="prism  language-java">DateTimeFormatter f <span class="token operator">=</span>
    DateTimeFormatter<span class="token punctuation">.</span><span class="token function">ofPattern</span><span class="token punctuation">(</span><span class="token string">"dd-MM-yyyy HH:mm"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

String s <span class="token operator">=</span> dateTime<span class="token punctuation">.</span><span class="token function">format</span><span class="token punctuation">(</span>f<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-common-patterns">🔹 Common Patterns</h2>

<table>
<thead>
<tr>
<th>Pattern</th>
<th>Meaning</th>
</tr>
</thead>
<tbody>
<tr>
<td>dd</td>
<td>day</td>
</tr>
<tr>
<td>MM</td>
<td>month</td>
</tr>
<tr>
<td>yyyy</td>
<td>year</td>
</tr>
<tr>
<td>HH</td>
<td>hour</td>
</tr>
<tr>
<td>mm</td>
<td>minute</td>
</tr>
</tbody>
</table><hr>
<h1 id="🔄-7.-parse-string-→-date">🔄 7. PARSE STRING → DATE</h1>
<h2 id="🔹-use-case-input-handling">🔹 Use case: input handling</h2>
<pre class=" language-java"><code class="prism  language-java">LocalDateTime dt <span class="token operator">=</span>
    LocalDateTime<span class="token punctuation">.</span><span class="token function">parse</span><span class="token punctuation">(</span><span class="token string">"20-04-2025 10:30"</span><span class="token punctuation">,</span>
        DateTimeFormatter<span class="token punctuation">.</span><span class="token function">ofPattern</span><span class="token punctuation">(</span><span class="token string">"dd-MM-yyyy HH:mm"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🌍-8.-time-zones-very-important">🌍 8. TIME ZONES (VERY IMPORTANT)</h1>
<h2 id="🔹-use-case-global-apps">🔹 Use case: global apps</h2>
<pre class=" language-java"><code class="prism  language-java">ZonedDateTime zdt <span class="token operator">=</span>
    ZonedDateTime<span class="token punctuation">.</span><span class="token function">now</span><span class="token punctuation">(</span>ZoneId<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token string">"Asia/Kolkata"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔁-convert-timezone">🔁 Convert timezone</h2>
<pre class=" language-java"><code class="prism  language-java">zdt<span class="token punctuation">.</span><span class="token function">withZoneSameInstant</span><span class="token punctuation">(</span>ZoneId<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token string">"America/New_York"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⏳-9.-find-difference">⏳ 9. FIND DIFFERENCE</h1>
<h2 id="🔹-use-case-duration-age">🔹 Use case: duration, age</h2>
<h3 id="date-difference">Date difference</h3>
<pre class=" language-java"><code class="prism  language-java">Period p <span class="token operator">=</span> Period<span class="token punctuation">.</span><span class="token function">between</span><span class="token punctuation">(</span>startDate<span class="token punctuation">,</span> endDate<span class="token punctuation">)</span><span class="token punctuation">;</span>
p<span class="token punctuation">.</span><span class="token function">getDays</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
p<span class="token punctuation">.</span><span class="token function">getMonths</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
p<span class="token punctuation">.</span><span class="token function">getYears</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h3 id="time-difference">Time difference</h3>
<pre class=" language-java"><code class="prism  language-java">Duration d <span class="token operator">=</span> Duration<span class="token punctuation">.</span><span class="token function">between</span><span class="token punctuation">(</span>startTime<span class="token punctuation">,</span> endTime<span class="token punctuation">)</span><span class="token punctuation">;</span>
d<span class="token punctuation">.</span><span class="token function">toHours</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
d<span class="token punctuation">.</span><span class="token function">toMinutes</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔧-10.-modify-date-immutable">🔧 10. MODIFY DATE (IMMUTABLE!)</h1>
<h2 id="🔹-use-case-adjustments">🔹 Use case: adjustments</h2>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">withDayOfMonth</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">withMonth</span><span class="token punctuation">(</span><span class="token number">12</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
date<span class="token punctuation">.</span><span class="token function">withYear</span><span class="token punctuation">(</span><span class="token number">2026</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="📌-11.-check-conditions">📌 11. CHECK CONDITIONS</h1>
<h2 id="🔹-use-case-validation">🔹 Use case: validation</h2>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">isLeapYear</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

date<span class="token punctuation">.</span><span class="token function">getDayOfWeek</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">==</span> DayOfWeek<span class="token punctuation">.</span>SUNDAY<span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔗-12.-combine-date--time">🔗 12. COMBINE DATE + TIME</h1>
<h2 id="🔹-use-case-scheduling">🔹 Use case: scheduling</h2>
<pre class=" language-java"><code class="prism  language-java">LocalDateTime dt <span class="token operator">=</span>
    LocalDateTime<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span>date<span class="token punctuation">,</span> time<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🧠-13.-key-concept-very-important">🧠 13. KEY CONCEPT (VERY IMPORTANT)</h1>
<p>👉 All classes are <strong>IMMUTABLE</strong></p>
<pre class=" language-java"><code class="prism  language-java">date<span class="token punctuation">.</span><span class="token function">plusDays</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">// ❌ no change</span>
date <span class="token operator">=</span> date<span class="token punctuation">.</span><span class="token function">plusDays</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// ✅ correct</span>

</code></pre>
<hr>
<h1 id="⚠️-common-mistakes">⚠️ COMMON MISTAKES</h1>
<ol>
<li>
<p>❌ Forgetting immutability</p>
</li>
<li>
<p>❌ Wrong formatter pattern</p>
</li>
<li>
<p>❌ Ignoring timezone</p>
</li>
<li>
<p>❌ Using old <code>Calendar</code></p>
</li>
<li>
<p>❌ Confusing <code>Period</code> vs <code>Duration</code></p>
</li>
</ol>
<hr>
<h1 id="🧠-final-memory-map">🧠 FINAL MEMORY MAP</h1>
<ul>
<li>
<p>Create → <code>now()</code>, <code>of()</code>, <code>parse()</code></p>
</li>
<li>
<p>Modify → <code>plus()</code>, <code>minus()</code>, <code>with()</code></p>
</li>
<li>
<p>Compare → <code>isBefore()</code>, <code>isAfter()</code></p>
</li>
<li>
<p>Format → <code>DateTimeFormatter</code></p>
</li>
<li>
<p>Timezone → <code>ZonedDateTime</code></p>
</li>
<li>
<p>Difference → <code>Period</code>, <code>Duration</code></p>
</li>
</ul>
<hr>
<h1 id="🎯-20-second-interview-answer">🎯 20-SECOND INTERVIEW ANSWER</h1>
<p>👉<br>
“Java’s java.time API provides immutable classes like LocalDate, LocalTime, and ZonedDateTime for handling date and time. It supports creation, manipulation, formatting, parsing, and timezone handling, making it a robust replacement for legacy date APIs.”</p>
<hr>
<hr>
<h1 id="🚀-1.-java-streams-core-idea">🚀 1. Java Streams (Core Idea)</h1>
<p>👉 Stream = <strong>process data (collections) in a functional way</strong></p>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span> → operations → result

</code></pre>
<hr>
<h2 id="🧠-key-properties">🧠 Key Properties</h2>
<ul>
<li>
<p>No data storage (just pipeline)</p>
</li>
<li>
<p>Immutable (doesn’t change original collection)</p>
</li>
<li>
<p>Lazy execution</p>
</li>
</ul>
<hr>
<h1 id="🔥-2.-stream-pipeline-very-important">🔥 2. Stream Pipeline (VERY IMPORTANT)</h1>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">&gt;</span> <span class="token number">10</span><span class="token punctuation">)</span>   <span class="token comment">// intermediate</span>
    <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">*</span> <span class="token number">2</span><span class="token punctuation">)</span>       <span class="token comment">// intermediate</span>
    <span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// terminal</span>

</code></pre>
<hr>
<h2 id="⚡-types-of-operations">⚡ Types of Operations</h2>

<table>
<thead>
<tr>
<th>Type</th>
<th>Examples</th>
</tr>
</thead>
<tbody>
<tr>
<td>Intermediate</td>
<td><code>filter</code>, <code>map</code>, <code>sorted</code></td>
</tr>
<tr>
<td>Terminal</td>
<td><code>forEach</code>, <code>collect</code>, <code>count</code></td>
</tr>
</tbody>
</table><hr>
<h1 id="🔥-3.-most-important-stream-methods">🔥 3. Most Important Stream Methods</h1>
<hr>
<h2 id="🔹-filter-→-remove-unwanted-data">🔹 filter() → remove unwanted data</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-map-→-transform-data">🔹 map() → transform data</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">*</span> x<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-sorted">🔹 sorted()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">sorted</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-foreach-→-printprocess">🔹 forEach() → print/process</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-collect-→-convert-to-list">🔹 collect() → convert to list</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">collect</span><span class="token punctuation">(</span>Collectors<span class="token punctuation">.</span><span class="token function">toList</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-count">🔹 count()</h2>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">long</span> c <span class="token operator">=</span> list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">count</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-limit--skip">🔹 limit() / skip()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">limit</span><span class="token punctuation">(</span><span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">skip</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-findfirst">🔹 findFirst()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">findFirst</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-anymatch">🔹 anyMatch()</h2>
<pre class=" language-java"><code class="prism  language-java">list<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">anyMatch</span><span class="token punctuation">(</span>x <span class="token operator">-</span><span class="token operator">&gt;</span> x <span class="token operator">&gt;</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚡-4.-real-example">⚡ 4. Real Example</h1>
<pre class=" language-java"><code class="prism  language-java">List<span class="token operator">&lt;</span>Integer<span class="token operator">&gt;</span> nums <span class="token operator">=</span> List<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token number">1</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">3</span><span class="token punctuation">,</span><span class="token number">4</span><span class="token punctuation">,</span><span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

nums<span class="token punctuation">.</span><span class="token function">stream</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">filter</span><span class="token punctuation">(</span>n <span class="token operator">-</span><span class="token operator">&gt;</span> n <span class="token operator">%</span> <span class="token number">2</span> <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>n <span class="token operator">-</span><span class="token operator">&gt;</span> n <span class="token operator">*</span> n<span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">forEach</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚠️-common-mistakes-1">⚠️ Common Mistakes</h1>
<ol>
<li>
<p>❌ Forgetting terminal operation</p>
</li>
<li>
<p>❌ Modifying original list</p>
</li>
<li>
<p>❌ Overusing streams for simple loops</p>
</li>
</ol>
<hr>
<h1 id="🧠-memory-flow">🧠 MEMORY FLOW</h1>
<p>👉<br>
<strong>filter → map → collect</strong></p>
<hr>
<h1 id="🚀-5.-optional-core-idea">🚀 5. Optional (Core Idea)</h1>
<p>👉 Avoid <strong>NullPointerException</strong></p>
<pre class=" language-java"><code class="prism  language-java">Optional<span class="token operator">&lt;</span>String<span class="token operator">&gt;</span> opt <span class="token operator">=</span> Optional<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span><span class="token string">"Hello"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔥-6.-create-optional">🔥 6. Create Optional</h1>
<pre class=" language-java"><code class="prism  language-java">Optional<span class="token punctuation">.</span><span class="token function">of</span><span class="token punctuation">(</span>value<span class="token punctuation">)</span><span class="token punctuation">;</span>        <span class="token comment">// NOT null</span>
Optional<span class="token punctuation">.</span><span class="token function">ofNullable</span><span class="token punctuation">(</span>val<span class="token punctuation">)</span><span class="token punctuation">;</span>  <span class="token comment">// may be null</span>
Optional<span class="token punctuation">.</span><span class="token function">empty</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="🔥-7.-most-important-methods">🔥 7. Most Important Methods</h1>
<hr>
<h2 id="🔹-ispresent">🔹 isPresent()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">isPresent</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-get-⚠️-risky">🔹 get() (⚠️ risky)</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">get</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span> <span class="token comment">// exception if empty</span>

</code></pre>
<hr>
<h2 id="🔹-orelse">🔹 orElse()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">orElse</span><span class="token punctuation">(</span><span class="token string">"Default"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-orelseget">🔹 orElseGet()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">orElseGet</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">-</span><span class="token operator">&gt;</span> <span class="token string">"Default"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-orelsethrow">🔹 orElseThrow()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">orElseThrow</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-ifpresent">🔹 ifPresent()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">ifPresent</span><span class="token punctuation">(</span>System<span class="token punctuation">.</span>out<span class="token operator">:</span><span class="token operator">:</span>println<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h2 id="🔹-map">🔹 map()</h2>
<pre class=" language-java"><code class="prism  language-java">opt<span class="token punctuation">.</span><span class="token function">map</span><span class="token punctuation">(</span>String<span class="token operator">:</span><span class="token operator">:</span>toUpperCase<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚡-8.-real-example">⚡ 8. Real Example</h1>
<pre class=" language-java"><code class="prism  language-java">Optional<span class="token operator">&lt;</span>String<span class="token operator">&gt;</span> name <span class="token operator">=</span> Optional<span class="token punctuation">.</span><span class="token function">ofNullable</span><span class="token punctuation">(</span>null<span class="token punctuation">)</span><span class="token punctuation">;</span>

String result <span class="token operator">=</span> name<span class="token punctuation">.</span><span class="token function">orElse</span><span class="token punctuation">(</span><span class="token string">"Guest"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

System<span class="token punctuation">.</span>out<span class="token punctuation">.</span><span class="token function">println</span><span class="token punctuation">(</span>result<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre>
<hr>
<h1 id="⚠️-common-mistakes-2">⚠️ Common Mistakes</h1>
<ol>
<li>
<p>❌ Using <code>get()</code> blindly</p>
</li>
<li>
<p>❌ Using Optional in fields (not recommended)</p>
</li>
<li>
<p>❌ Ignoring <code>orElse()</code></p>
</li>
</ol>
<hr>
<h1 id="🧠-final-memory-map-1">🧠 FINAL MEMORY MAP</h1>
<h2 id="streams-1">Streams:</h2>
<ul>
<li>
<p>filter → map → collect</p>
</li>
<li>
<p>intermediate + terminal</p>
</li>
</ul>
<h2 id="optional">Optional:</h2>
<ul>
<li>
<p>of / ofNullable</p>
</li>
<li>
<p>orElse / ifPresent</p>
</li>
<li>
<p>avoid null</p>
</li>
</ul>
<hr>
<h1 id="🎯-20-second-interview-answer-1">🎯 20-SECOND INTERVIEW ANSWER</h1>
<p>👉<br>
“Streams in Java provide a functional approach to process collections using operations like filter, map, and collect, while Optional is a container object used to handle null values safely and avoid NullPointerException.”</p>
<hr>

