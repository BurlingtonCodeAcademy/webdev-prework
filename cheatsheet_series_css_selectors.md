# CSS Selectors

CSS Selectors are your way of targeting the elements in your HTML that you require, and nothing more. On their own, they allow you to identify specific `id`s, entire `class`es, and even all elements that share a given name. This reference guide serves as a quick resource to help you target what you need, and nothing more.


For a full list of resources, check out this list.

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors">MDN: CSS Selectors </a>

## Basic Selectors

<table>

<th>Selector</th>
<th>Target</th>
<th>Example</th>

<tr>
<td>type</td>
<td>Selects all elements with the given tag name</td>
<td>

```css
div {
/* targets all divs */
}
```
</td>
</tr>


<tr>
<td>.class</td>
<td>Selects all elements with the given class name</td>
<td>

```css
.my-class {
/* targets all elements with class "my-class" */
}
```
</td>
</tr>

<tr>
<td>#id</td>
<td>Targets a single element with the given id name</td>
<td>

```css
#my-id {
/* targets the element with id "my-id"*/
}
```
</td>
</tr>

<tr>
<td>[attribute]</td>
<td>Targets all elements with the given attribute</td>
<td>

```css
[hidden] {
/* targets all elements with "hidden" attribute*/
}
```
</td>
</tr>

<tr>
<td>*</td>
<td>Targets everything</td>
<td>

```css
#my-id {
/* targets the element with id "my-id"*/
}
```
</td>
</tr>
</table>

<br/>

## Combinators

<table>

<th>Selector</th>
<th>Target</th>
<th>Example</th>

<tr>
<td>Descendent (" ")</td>
<td>Selects all elements to the right of the whitespace that are children of the element to the left.</td>
<td>

```css
div p {
/* targets all <p> elements that are inside of a <div> */
}
```
</td>
</tr>


<tr>
<td>,</td>
<td>Separates different selector types</td>
<td>

```css
div,.my-class {
/* targets all divs, AND all elements with the class "my-class" */
}
```
</td>
</tr>

<tr>
<td>element.class</td>
<td>Targets all elements that match the type and class</td>
<td>

```css
div.my-class {
/* targets all divs with the class, "my-class"*/
}
```
</td>
</tr>

<tr>
<td>Adjacent Sibling (+)</td>
<td>Selects an element immediately following another</td>
<td>

```css
div + p {
/* targets the first <p> element that is placed immediately after a <div>. */
}
```
</td>
</tr>

<tr>
<td>Child (>)</td>
<td>Selects elements that are direct children of the first element. </td>
<td>

```css
div > p {
/* targets <p> elemets that are one-level lower than their containing <div>*/
}
```
</td>
</tr>


<tr>
<td>General Sibling (~)</td>
<td>Selects sibling elements. Selects elements that share a parent element. </td>
<td>

```css
div ~ p {
/* targets all <p> elements that follow a <div> AND are its siblings*/
}
```
</td>
</tr>
</table>

<br/>


## Pseudo-Classes

There are many, many pseudo-classes (and more every day!). Visit [MDN's Pseudo-class list](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) for a complete rundown. In the meantime, here are some of the most common.

<table>

<th>Selector</th>
<th>Target</th>
<th>Example</th>

<tr>
<td>:hover</td>
<td>Applies relevant CSS to the targeted element(s) when your mouse is positioned over them</td>
<td>

```css
.myclass:hover {
/* Apply these styles to elements with class "myclass" ONLY when hovered over. */
}
```
</td>
</tr>


<tr>
<td>:active</td>
<td>Applies CSS to element that has been "activated". Circumstantial. Oftentimes, when clicked.</td>
<td>

```css
a:active{
/* Apply these styles to <a> elements when they are clicked. */
}
```
</td>
</tr>

<tr>
<td>:focus</td>
<td>Applies CSS to element that has the focus of the browser.</td>
<td>

```css
input:focus {
/* Apply these styles to an <input> element when they are focused*/
}
```
</td>
</tr>

<tr>
<td>:nth-child</td>
<td>Takes An+B structure to determine selection pattern of child elements</td>
<td>

```css
div:nth-child(4n+3){
/* Selects 3rd <div> element, and then every 4th after that. */
}
```
</td>
</tr>

<tr>
<td>:disabled</td>
<td>Selects elements that have been disabled, like buttons and other inputs. </td>
<td>

```css
a:disabled {
/*Apply these styles to an element that has been disabled.*/
}
```
</td>
</tr>


<tr>
<td>:not</td>
<td>Selects all elements EXCEPT the targeted selector. </td>
<td>

```css
:not(div) {
/* targets all elements that are <div> elements.*/
}
```
</td>
</tr>
</table>

<br/>

