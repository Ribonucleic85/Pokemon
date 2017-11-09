/*
 css based element finders

 'sel' does a global search and
 finds any elements matched in
 the DOM and returns them as an
 array

 USE:
    sel( "css_selectors" );
 --------------------------------

 'rSel' finds elements related
 to 'sel[n]' or any chosen
 element and returns them as an
 array
 
 notes
 * the third and forth examples of 'rSel'
 * can be chained as shown in the
 * fifth (labeled 'EXT' for 'EXTended USE')
 * note that the first instance of 'rSel'
 * in the chain has '[n]' to select one
 * of the returned elements
 USE:
      rSel( element, "css_selectors" );
 OR:  rSel( sel[n], "css_selectors" );
 OR:  element.rSel( "css_selectors" );
 OR:  sel[n].rSel( "css_selectors" );
 EXT: element.rSel( "css_selectors" )[n].rSel( "css_selectors" );
*/

function sel(q) {
  return document.querySelectorAll(q);
}

function rSel(e,q) {
  return e.querySelectorAll(q);
}

Element.prototype.rSel = function(q) {
  return this.querySelectorAll(q);
}

/********************************************************************/
/*
 --- incomplete code ---
 pokemon type selection based on url
 this makes use of 'sel' and 'rSel'
 from above
*/


var typeseg = ["https://www.serebii.net/pokedex-sm/", ".shtml"],
types = [
  "bug",      "dark",  "dragon", "electric", "fairy",
  "fighting", "fire",  "flying", "ghost",    "grass",
  "ground",   "ice",   "normal", "poison",   "psychic",
  "rock",     "steel", "water"
],

s = [".dextable > * > tr", " > td"];

(typeseg[0] +types[0]+ typeseg[1])
== sel( s[0] )[2]
 .rSel( s[0]+s[1] )[3]
 .rSel( "A" )[0].href;
  
/********************************************************************/
/*
 --- incomplete code ---
 code for looping through table rows
 in Pokemon by Type pages on Serebii
*/
var lim = byId('testrow').getElementsByTagName('tr').length-1;
var dn, ty, c;

for ( c=2;  c<lim;  c++ ) {
    dn = byId('testrow').getElementsByTagName('tr')[c].getElementsByTagName('td')[0].innerHTML;
}
