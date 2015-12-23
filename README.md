#jQuery.path
Provides animation along bezier and circular arcs.<br>

The animation engine in jQuery is focussed on single dimensional animation - hence it's difficult to animate two variables along a path.<br>

This simple plugin provides a method of multidimensional animation, and in particular provides a method for animating along bezier curves and arcs.<br>

#Bezier

Example: animate along a bezier path<br>

var bezier_params = {
    start: { 
      x: 185,<br>
      y: 185,<br> 
      angle: 10<br>
    },  <br>
    end: { <br>
      x:540,<br>
      y:110, <br>
      angle: -10, <br>
      length: 0.25<br>
    }<br>
  }<br>
  
$("my_elem").animate({path : new $.path.bezier(bezier_params)})<br>
Bezier curves are made form a start point, an end point each with a control point<br>

start is starting point<br>
end is the final point<br>
x,y indicate the coordinates at that point. Required<br>
angle is the angle of the control point from the line joining the start and end. Optional, default is 0<br>
length is the distance from the point to it's control point as a ratio of the distance from start to end. Optional, default is 1/3<br>
#Arc

Exampe: animate along an arc<br>

  
var arc_params = {<br>
    center: [285,185],  <br>
        radius: 100,   <br> 
        start: 30,<br>
        end: 200,<br>
        dir: -1<br>
  }<br>
  
$("my_elem").animate({path : new $.path.arc(arc_params)})<br>
center is the coords of the centre of an imaginary circle that contains the start and end point<br>
radius is the radius of this circle<br>
start is the angle of the start point. 0 is "North", measured clockwise<br>
end is the angle of the start point. 0 is "North", measured clockwise<br>
dir is the direction to move in. Only required if not obvious from start and end (e.g. if start is 100, end is 30, but you want to animate clockwise)<br>
#Other Paths

It is trivial to create other paths, or even animate other parameters. E.g:<br>

var SineWave = function() {<br>
  this.css = function(p) {<br>
    var s = Math.sin(p*20)<br>
    var x = 500 - p * 300 <br>
    var y = s * 50 + 150<br>
    var o = ((s+2)/4+0.1)<br>
    return {top: y + "px", left: x + "px", opacity: o}<br>
  } <br>
};
  <br>
$("my_elem").animate({path : new SineWave})<br>
