# draft

## About

draft is a simple drafting module for [LÖVE 2D](https://love2d.org/). It makes it easy to draft primitive shapes, and some more luxurious ones.

## Loading the module

To load the module, use the following code.

    local draft = require('draft')
    draft = draft(_mode_)

Setting _mode_ is optional. The default is _fill_.

The drafting functions can then be called inside the `love.draw()` function.

## Usage example

    local draft = require('draft')
    draft = draft()
    
    function love.draw()
        draft:rectangle(210, 30, 50, 30, 'line')
        draft:bow(200, 200, 50, 2)
        local vertices = draft:square(400, 200, 300, 'line')
        draft:linkWeb(vertices)
    end

## Notes

 - The _mode_ can be set when initializing the module, but it can also be overwritten with each drafting function. If you want to overwrite it for many functions, you can use the `draft:getMode` and `draft:setMode` functions.

 - You can also set the _mode_ to _false_ if you only want to get the vertices, and not draw the shape. For example, using the following code would get the vertices for a rectangle without drawing it.

    `local vertices = draft:rectangle(100, 100, 50, 80, false)`

 - Look at the file _test.lua_ for examples on how the functions can be called. This file draws all the possible shapes.

 - Due to LÖVE 2D drawing limitations, the `draft:star` function fails in _fill mode_. This is because LÖVE 2D is unable to properly fill concave polygons.

 - The `draft:compass` function is a powerful function used to draw curves. Notably, it accepts a function for the scale parameter which permits the drawing of complex shapes. You can look at the code for `draft:star` and `draft:egg` for examples of usage. You can also look at the `draft:compass` function too see how it is called. The parameters are (x, y, i, numSegments).

 - The linkers create line between points.

## Draft function list

### Initialization
draft(mode)  

### Getters and Setters
draft:getMode()  
draft:setMode(mode)  

### Shapes
draft:line(points, mode)  
draft:triangleIsosceles(cx, cy, width, height, mode)  
draft:triangleRight(cx, cy, width, height, mode)  
draft:rectangle(cx, cy, width, height, mode)  
draft:polygon(vertices, mode)  
draft:triangleEquilateral(cx, cy, width, mode)  
draft:square(cx, cy, length, mode)  
draft:trapezoid(cx, cy, width, height, widthTop, widthTopOffset, mode)  
draft:rhombus(cx, cy, width, height, mode)  
draft:trapezium(cx, cy, widthLeft, widthRight, height, depth, mode)  
draft:gem(cx, cy, widthTop, widthMiddle, height, depth, mode)  
draft:diamond(cx, cy, width, mode)  
draft:rhombusEquilateral(cx, cy, length, mode)  
draft:lozenge(cx, cy, width, mode)  
draft:kite(cx, cy, width, height, depth, mode)  
draft:trapezoidIsosceles(cx, cy, width, height, widthTop, mode)  
draft:parallelogram(cx, cy, width, height, widthOffset, mode)  
draft:compass(cx, cy, width, arcAngle, startAngle, numSegments, wrap, scale, mode)  
draft:circle(cx, cy, radius, numSegments, mode)  
draft:arc(cx, cy, radius, arcAngle, startAngle, numSegments, mode)  
draft:bow(cx, cy, radius, arcAngle, startAngle, numSegments, mode)  
draft:pie(cx, cy, radius, arcAngle, startAngle, numSegments, mode)  
draft:ellipse(cx, cy, width, height, numSegments, mode)  
draft:ellipticArc(cx, cy, width, height, arcAngle, startAngle, numSegments, mode)  
draft:ellipticBow(cx, cy, width, height, arcAngle, startAngle, numSegments, mode)  
draft:ellipticPie(cx, cy, width, height, arcAngle, startAngle, numSegments, mode)  
draft:semicircle(cx, cy, width, startAngle, numSegments, mode)  
draft:dome(cx, cy, width, startAngle, numSegments, mode)  
draft:star(cx, cy, width, widthInner, numPoints, startAngle, mode)  
draft:egg(cx, cy, width, syBottom, syTop, numSegments, mode)

### Linkers
draft:linkLadder(v1, v2, mode)  
draft:linkTangle(v1, v2, mode)  
draft:linkWeb(v, mode)  
draft:linkTangleWebs(v1, v2, mode)
