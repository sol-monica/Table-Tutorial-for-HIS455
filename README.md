# Writing Tables into your code with HTML & CSS

Tables are a useful way to organize information. Creating tables in HTML is simple enough, however,
customizing your tables  can prove to be tricky. The purpose of this tutorial is to guide you through
the elementary processes of creating, and customizing tables in HTML and CSS.

I have separated the tutorial into two parts:
1. Creating tables
2. Styling tables

You can probably get away with just reading 1., but I would highly recommend learning 2. as well. I've tried to include only the basics. Let's get started!

## 1. Creating Tables in HTML

In HTML, tables are defined with the tag `<table>`.

To define separate rows, use ``<tr>`` for each respective row, within the ``<table>`` tag.

And to further define the cells of each row, enclose your cell contents with ``<td>``. Headings are special,
they get a ``<th>`` tag.

``<table>``, ``<tr>``, ``<th>``, and ``<td>`` are the basic tags to create a simple, barebones table. See below!


``` html
<table> <!-- Starting the table here -->

	<!-- First row -->
	<tr>
		<th>Class</th> <!-- First heading ... -->
		<th>Assignment</th>
		<th>Mark</th>
	</tr>  <!--- So this table has three headings, which equals three columns! -->

	<!-- Second Row -->
	<tr>
		<td>EAS449</td>
		<td>Presentation</td>
		<td>A</td>
	</tr>

	<!-- Third Row -->
	<tr>
		<td>EAS417</td>
		<td>Final Project</td>
		<td>A+</td>
	</tr>

</table>
```
The resulting table does not have any borders by default.

Use `<table>` to denote the start of the table.
`<tr>` determines a row, `<th>` a heading (essentially a column), and `<td>` the contents of an individual cell. Don't forget to close the tags!

### 2. Styling Tables using CSS&HTML (but mostly CSS)

Creating tables with your content seems easy enough. You may also find it useful to customize the cell contents or the actual table.

For the purposes of this tutorial, I have included a few essential customizations:
1. [Titles](#titles)
2. [Borders](#borders)
3. [Merged cells](#merged)
4. [Content](#content)
5. [Sizing and Spacing](#sz)

#### 2.1 Titles <a id="titles"></a>

You can label your table with a `<caption>` tag, which **must be inserted immediately after** the `<table>` tag in the **HTML**.

The CSS properties `text-align` or `caption-side` can be used to change the alignment of the title. You can alter other qualities such as colour, weight, and font in CSS, under the `caption{}` selector.

The following snippet inserts a caption, which is automatically centered. Something like `caption{text-align:left;}` aligns the title to the left.
``` HTML
<table>
	<caption> Term One Grades 2016 </caption> <!-- Here's my title -->
	<tr>
		<th>Class</th><th>Assignment</th><th>Mark</th>
	</tr>  
	<tr>
		<td>EAS449</td><td>Presentation</td><td>A</td>
	</tr>
	<tr>
		<td>EAS417</td><td>Final Project</td><td>A+</td>
	</tr>
</table>
```

#### 2.2 Borders <a id="borders"></a>

Borders are important in giving tables an organized look. The values of the `border` property will be able to change the style of the border (line weight, type, and colour). You can change the borders of the entire table, cells, or headings, depending on the selectors you use.

``` CSS
table, td, th {
	border: 2px solid red;
}
```
The result is a table with solid borders of 2px weight and red in colour. If you just used `table{}` selector, the properties would apply to the outermost borders only. Since `table, td, th {}` are selected, borders apply to all those cells.

By default, the borders are "separated". The default result looks like a double border all around. To collapse them into a conventional single line border, use `border-collapse`:

```CSS
table {
    border-collapse: collapse;
}
```

#### 2.3 Merged cells <a id="merged"></a>

Sometimes you may want to have cells that span multiple rows or columns.
To have a cell span multiple columns, use `colspan`. To have a cell span multiple rows, use `rowspan`.
This bit of code should be added to the specific `<td>` you want to span **within the HTML.**

``` HTML
<table>
	<caption> Term One Grades 2016 </caption>
	<tr>
		<th>Class</th>
		<th>Assignment</th>
		<th>Mark</th>
	</tr>  
	<tr>
		<td>EAS449</td>
		<td>Presentation</td>
		<td>A</td>
	</tr>
	<tr>
		<td>EAS417</td>
		<td>Final Project</td>
		<td>A+</td>
	</tr>
  <tr>
		<td rowspan="2">EAS372</td> <!-- So this cell will span two rows, encompassing the row directly below it-->
		<td> Essay One </td>
		<td> B+</td>
	</tr>
  <tr>
		<!-- Note absence of a <td> here. We don't need it because EAS372 spans this row! -->
		<td> Essay Two </td>
		<td> A</td>
	</tr>
</table>
```
This produces a table where EAS372 spans **two rows**, including Essay One and Essay Two.

#### 2.4 Content <a id="content"></a>

##### Text
You can change the alignment of the text within `<th>` or `<td>`. Use `vertical-align` to change the vertical alignment of the text to `top`, `bottom`, or `middle`.
Use `text-align` to change the horzontal alignment of the text to `left`, `center`, or `right`.

By default, contents of `<th>` will be aligned in the center, and `<td>` will be aligned to the left.

The below snippet of code would align the text to be exactly in the center of its respective cell.
```CSS
td, th {
	vertical-align: middle;
	text-align: center;
}
```
##### Background Colour
You can also change, say, the `background-color` of `<th>`. Similarly, you can change `background-color` of each row `<tr>` and even individual cells `<td>`!

Although you can change these in the CSS, if you are changing simply one row, or one cell, it might be easier to include it in the HTML, using a snippet such as `<td style="background-color:red">EAS449</td>` to colour a single `<td>` for example.

#### 2.5 Sizing and Spacing <a id="sz"></a>

##### Dimensions
It is also helpful to change the dimensions of your table, as well as the spacing of each cell or row. You can do so using `width` and `height`.

The following snippet means that the width of the entire table will be equal to 100% , and the height of `<th>` will be 60px.
```CSS
table {
    width: 100%;
}

th {
    height: 60px;
}
```

##### Padding
Padding refers to the area in between the content and the table border. You can use `padding` to control the size of the area, giving your table a spacious look.

The following snippet sets the padding of each cell, `<td>` and `<th>` to 20px. Roomy!

```CSS
th, td {
	padding: 20px;
}
```
#### Positioning
To position your table, use `margin` and `float` as usual. I won't include too many details on this since someone else may have written a tutorial on this.

To set the table in the center of the page, set left and right margins to `auto`.  

To set the table to the left, or right of other text on the page, use `float:left;` and `float:right;` respectively.

## Summary
Some new tags and selectors of the above tutorial are summarized in a table, below. I didnt include much of the text positioning, or colouring, since those are pretty universal -- you just need to be mindful of where you put them.

| Code | Description | HTML or CSS? |
|-----|-------------|--------------|
| `<table>` | Creates the table | HTML |
|`<caption>`| Insert a title with this | HTML |
|`<th>`| Defines the headings of each column | HTML |
|`<tr>`| Defines when a new row begins | HTML |
|`<td>`| Defines a single cell and its contents | HTML |
|`border:`| Border property, can define line style | CSS |
|`colspan`| To have a cell span several columns | HTML |
|`rowspan`| To have a cell span several rows | HTML |
|`padding`| Determine the space between content and border | CSS

While I've included the basics in this tutorial; there are many, many, more ways in which you can customize the style of your table even further. [Here](https://www.w3schools.com/css/css_table.asp) is a link to where you can read more about that, especially closer to the bottom of the page.

## Self-Test

Here's some data.

Create and customize a table that lists each book, its author, and whether it has a film adaptation.

* Harry Potter and the Chamber of Secrets by J.K. Rowling
* Harry Potter and the Sorcerer's Stone by J.K. Rowling
* Kafka on the Shore by Haruki Murakami
* The Good Earth by Pearl S. Buck
* In Search of Lost Time by Marcel Proust
* Discipline and Punish by Michel Foucault

Try the following:
1. Make sure each data point has its own cell
2. Add borders to the table.
3. Make the heading row a different colour.
4. Center the text within each cell, vertically and horizontally.
5. Make J.K. Rowling span two rows, for both her HP titles!

Make it easy on the eyes!

[Here's a link to a jsbin where I've set up some of the basics.](http://jsbin.com/yujojicutu/edit?html,css,output)


 <!--
 og: (http://jsbin.com/yujojicutu/edit?html,css,output)
 solution: http://jsbin.com/demiwovowi/edit?html,css,output -->
