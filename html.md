[mobilege](/README.md#web)
/ [HTML](/html.md) 
    <sub>&nbsp;&nbsp;[Docs](https://developer.mozilla.org/en-US/docs/Web/HTML)</sub>
    
# HTML
## Elements
```html
<!-- Bold -->
<!-- Emmet shortcut: b -->
<b>This is bold</b>


<!-- Paragraph -->
<!-- Emmet shortcut: p -->
<p>This is a Paragraph.</p>


<!-- Heading -->
<!-- There should only be ONE h1 on a page. -->
<!-- Following content gets pushed to the next line automatically. -->
<!-- Emmet shortcut: h -->
<h1>This is a heading</h1>


<!-- Anchor -->
<!-- Emmet shortcut: a -->
<a href="page2.html">Page 2</a>
<a href="https://example.com">Website</a>


<!-- Image -->
<!-- Emmet shortcut: img -->
<img src="profile.jpeg" alt="Profile Photo">
<img src="https://upload.wikimedia.org/wikipedia/commons/b/bd/Golden_Retriever_Dukedestiny01_drvd.jpg"
    alt="Golden Retriever">


<!-- Comment -->
<!-- VSCode Shortcut: Cmd + /  -->
```


#### List
```html
<!-- List -->
<!-- Emmet shortcut: ol>ui*3 -->
<!-- Emmet shortcut: ol>ui* (Wraps existing text) -->
<ol>
    <li>Amadeus</li>
    <li>Stand By Me</li>
    <li>Amelie</li>
</ol>

<ul>
    <li>Alien</li>
    <li>Parasite</li>
    <li>Annie Hall</li>
</ul>
```

#### Table
```html
<!-- Table -->
<!-- Emmet shortcut: table>tr*2>td*3 (2 rows, 3 columns) -->
<table>
    <thead>
        <tr>
            <th>Subscription</th>
            <th>Price</th>
            <th>Support</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Free</td>
            <td>Free</td>
            <td>N/A</td>
        </tr>
        <tr>
            <td>Personal</td>
            <td>$9.99</td>
            <td>Weekdays</td>
        </tr>
        <tr>
            <td>Business</td>
            <td>$49.99</td>
            <td>27/7</td>
        </tr>
    </tbody>
</table>
```


#### Form
```html
<!-- form `action` attribute: The URL that processes the form submission. -->

<!-- label `for` attribute: Id of the associated form element.  -->

<!-- input `type` attribute eg: text, password, submit etc.  -->
<!-- input `name` attribute: Submitted with the form as part of a name/value pair. -->
<!-- input `value` attribute: Initial Value. -->

<body>
    <form action="page2.html">
        <label for="username"> Username </label>
        <input type="text" name="username" id="username" value="Initial Value">

        <label for="password"> Password </label>
        <input type="password" name="password" id="password">

        <input type="submit" value="Click to Submit!">
    </form>
```

###### Button behaviour inside & outside forms

```html
    <!-- By default, if a button is inside a form, it always submits the form when clicked. -->
    <form action="page2.html">
        <button>This button submits</button>
    </form>

    <!-- Only way to prevemt a button (inside a form) to not submit is to set its `type` attribute to "button" -->
    <form action="page2.html">
        <button type="button">This button doesn't submit</button>
    </form>
```

#### Semantic Elements

```html
    <!-- Used to group content so it can be easily styled -->
    <!-- Block-level -->
    <div>Some content here</div>

    <!-- Used to group elements for styling purposes -->
    <!-- Inline -->
    Some other contect. <span>This is inside span.</span>
```

```html
<body>

    <!-- Represents introductory content -->
    <header>This is a header</header>

    <!-- Provides navigation links -->
    <nav>
        These are nav elements.
        <a href="page1.html">Page 1</a>
        <a href="page2.html">Page 2</a>
        <a href="page3.html">Page 3</a>
    </nav>

    <!-- Content that is the central topic of a document -->
    <main>

        <!--  Independently distributable or reusable content -->
        <article>
            <h1>This is article header</h1>
            <p>This is article body</p>
        </article>

        <!-- Represents a generic standalone section of a document -->
        <!-- Should always have a heading -->
        <section>
            <h1>This is section 1 header</h1>
            <p>This is section 1 body</p>
        </section>

        <!-- Content is only indirectly related to the document's main content -->
        <!-- Eg. sidebars or call-out boxes -->
        <aside>
            <ul>
                <li>Aside list item 1</li>
                <li>Aside list item 2</li>
                <li>Aside list item 3</li>
                <li>Aside list item 4</li>
            </ul>
        </aside>
    </main>

    typically contains information about the author of the section, copyright data or links to related documents.

    <!-- Eg. author, copyright data, links etc -->
    <footer>This is a footer</footer>

</body>
```

## Resources
- [Emmet Cheat Sheet](https://docs.emmet.io/cheat-sheet/) &nbsp; · &nbsp;

## Shortcuts
- *Emmet: `opt + w` to wrap*
