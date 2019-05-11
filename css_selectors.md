Selector|Name|Example|Description
---|---|---|---
element|Element/Type/Tag|a|Select all a elements
\#id|ID|#123|Selects element with specific id="123"
a b|Descendant|#123 div|Selects all div (anywhere) inside of element with id="123"
.class|Class|div.intro|Selects all div elements with class="intro" (attribute)
[attribute]|Attribute|div[size]|Selects div elements with size attribute
[attribute="value"]|Attribute Value|div[size="10"][lang="en-US"]|Selects div elements with size="10" and lang="en-US"
[attribute^="value"]|Attribute Starts With|div[size^="10"]|Selects div elements with size attribute values starting with "10"
[attribute$="value"]|Attribute Ends With|div[size$="00"]|Selects div elements with size attribute values ending with "00"
[attribute*="value"]|Attribute Contains|div[size*="500"]|Selects div elements with size attribute values containing substring "500"
[attribute~="value]|Attribute Contains Word|div[size~="500"]|Selects the div elements with size attribute values containing word "500". " 500", "500 ", " 500 "
[attribute\|="value]|Attribute Contains Prefix|div[lang\|="en"]|Selects div elements with lang attribute starting with "en-" or matching "en".
a , b|Comma Combiner|div,.intro|Selects all div and all with class="intro"
\*|Universal|div *|Selects all elements inside all div
a + b|Adjacent Sibling|p+div|Selects div elements that immediately follow p elements
a ~ b|General Sibling|p~div|Selects div elements that follow p elements
a > b|Child|p > div|Selects div elements that are direct children of p elements
:first-child|First Child|p:first-child|Selects all first child elements that are p elements
:only-child|Only Child|p:only-child|Selects all only child elements that are p elements
:last-child|Last Child|p:last-child|Selects all last child elements that are p elements
:nth-child(n)|Nth Child|p:nth-child(2)|Selects all the second child elements that are p elements
:nth-last-child(n)|Nth Last Child|p:nth-last-child(2)|Selects all the second to last child elements that are p elements
:first-of-type|First of Type|p:first-of-type|Selects the first p elements
:nth-of-type(n)|Nth of Type|p:nth-of-type(2)|Selects the second p elements.  n can also be "even" or "odd" or "An+B" (every Ath element starting at and including Bth)
:only-of-type|Only of Type|p div:only-of-type|Selects div elements which are descendents of p if they are the only div element at a level
:last-of-type|Last of Type|div:last-of-type|Selects the last div elements
:empty|Empty|:empty|Elements with no children
:not(X)|Negation|div:not(.intro)|Selects div elements without class="intro"
