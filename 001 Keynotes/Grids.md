#coding #css #webdev 

[Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/grid) is a [[CSS]] style value for the display attribute. It is an alternative to flex-box, it uses the grid system to maintain and manipulate grid boxes.

It mainly uses 2 to 3 attributes apart from `display:grid;`
### Attribute
-  grid-template-columns / grid-template-row :  They mention how much spacing each column/row should take up and it is denoted with fr (Fractions).
- grid-row / gird-column: They mention how many grid spaces a container can take. It takes in a fraction (p/q) where `p = number of rows/columns of grid` and `q = place the container (q-1)th row/column of the grid` 
- gap: It mentions the gap between each gird element.
- grid-area:It is used on the child element to name the elements in grid templates. It takes in an input of "element name" to identify `grid-area: <element-name>`.
- grid-template-areas: It is used build custom grid templates. It takes in 3 parameters `grid-template-area: "<All elements names of the 1st row>" "<All elements names of the 2nd row>" "<All elements names of the 3rd row>" ...`
### Note:
- The `repeat(<iterations>,<fraction>/<itemsize (100px)>)` function can be used to repeat the same fraction to n number of iterations. 
- It can also have the parameters of `auto-fit` which should preceded with the `minmax(<elementsize>,<fraction>) `.
- One can use justify-content and align-items properties.





