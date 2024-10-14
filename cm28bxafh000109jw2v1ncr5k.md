---
title: "Essential Techniques for Drawing with Code on HTML Canvas"
seoTitle: "HTML Canvas: Drawing Techniques Explained"
seoDescription: "Master HTML Canvas to draw graphics, handle images, and create dynamic visuals with shapes, paths, text, and gradients"
datePublished: Mon Oct 14 2024 01:22:13 GMT+0000 (Coordinated Universal Time)
cuid: cm28bxafh000109jw2v1ncr5k
slug: essential-techniques-for-drawing-with-code-on-html-canvas
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1728868905088/2046a225-376b-4bd0-94e2-d51e9f845425.png
tags: javascript, web-development, html5, html-canvas

---

The HTML Canvas element is a powerful tool that enables web developers to draw graphics, manipulate images, and create dynamic visual content directly on web pages. Whether it's basic shapes, complex paths, or intricate effects, canvas opens up a world of creative possibilities for both simple illustrations and advanced interactive applications. In this blog, I’ll walk you through the essential concepts I learned from my recent LinkedIn Learning course on HTML Canvas, covering everything from drawing techniques to transformations and compositing methods. Whether you’re just getting started or looking to enhance your canvas skills.

### Draw rectangle

---

* **Rectangles are the basic shape**: On the Canvas, rectangles are the simplest shape you can draw. Other shapes like circles are built from rectangles.
    
* **Three main functions**:
    
    1. **clearRect**: This erases a rectangle area, making it transparent.
        
    2. **strokeRect**: This draws the outline of a rectangle with a specific color.
        
    3. **fillRect**: This fills the inside of a rectangle with a specific color.
        
* How it works :
    
    * **Starting Point**: You start drawing from the top-left corner of the rectangle.
        
    * **Dimensions**: You define the width (how wide) and height (how tall) of the rectangle.
        
* **Combining both**: You can also draw a rectangle that is both outlined and filled by using both `strokeRect` and `fillRect` with the same dimensions.
    

Example:

%[https://codepen.io/Annamalai-Palani/pen/mdNrewV] 

### Draw Line

---

1. **Moving the Pen**:
    
    * Think of an invisible pen that moves around the canvas.
        
    * `moveTo(x, y)`: Moves the pen to a specific spot but doesn't draw anything.
        
    * `lineTo(x, y)`: Draws a line from the current pen position to the new spot.
        
2. **Line Properties**:
    
    * `lineWidth`: Sets how thick the line should be.
        
    * `lineCap`: Decides how the ends of the line look (flat, rounded, or square).
        
    * `lineJoin`: Determines how corners are drawn when lines meet (rounded, beveled, or sharp).
        
3. **Drawing the Line**:
    
    * `beginPath()`: Starts a new drawing path.
        
    * `stroke()`: Actually draws the line based on the current path.
        
4. **Dashed Lines**:
    
    * `setLineDash([dash, gap])`: Creates dashed lines with specified lengths for dashes and gaps.
        
    * `getLineDash()`: Retrieves the current dash settings.
        
    * `lineDashOffset`: Adjusts where the dashes start.
        

---

Example :

%[https://codepen.io/Annamalai-Palani/pen/mdNreMV] 

---

### **Canvas State Overview**

---

* **Canvas State**: Think of it as a snapshot of all the current settings for drawing on the canvas. This includes properties like line width, stroke style, fill style, and more.
    

**Key Points**

1. **Drawing State**:
    
    * The canvas keeps track of various properties such as `lineWidth`, `strokeStyle`, `fillStyle`, etc.
        
    * It also tracks advanced properties like the transformation matrix and clipping region.
        
2. **Saving and Restoring State**:
    
    * **Why Save State?**: Imagine you have a complex drawing with many settings. You might want to temporarily change a setting without losing the original ones. Saving the state helps you revert back easily.
        
    * **How to Save State?**: Use `context.save()`. This pushes the current state onto a stack.
        
    * **How to Restore State?**: Use `context.restore()`. This pops the top state from the stack and makes it the current state.
        

**Analogy**

* **Stack of Papers**: Think of the canvas state as a stack of papers. Each paper represents a different set of drawing settings. When you save the state, you add a new paper to the stack. When you restore the state, you remove the top paper and go back to the previous one.
    

Example :

%[https://codepen.io/Annamalai-Palani/pen/XWvjmEo] 

### **Drawing Arcs**

---

* The `arc()` function requires parameters like center point (x, y), radius, start angle, end angle, and direction (clockwise or counterclockwise).
    
* Angles are measured in radians, not degrees.
    

Example :

%[https://codepen.io/Annamalai-Palani/pen/qBeaOMW] 

### **Paths Overview**

---

* **Path**: A path is a series of connected points on the canvas. It can be open (not connected back to the starting point) or closed (connected back to the starting point).
    

**Key Functions**

1. **Begin a Path**:
    
    * `ctx.beginPath()`: This function starts a new path. Think of it as picking up a pen and getting ready to draw.
        
2. **Move the Pen**:
    
    * `ctx.moveTo(x, y)`: Moves the pen to a specific point (x, y) on the canvas without drawing anything.
        
3. **Draw Lines**:
    
    * `ctx.lineTo(x, y)`: Draws a line from the current pen position to the new point (x, y).
        
4. **Stroke the Path**:
    
    * `ctx.stroke()`: Actually draws the lines you've defined in the path.
        
5. **Close the Path**:
    
    * `ctx.closePath()`: Closes the path by drawing a line back to the starting point.
        
6. **Fill the Path**:
    
    * `ctx.fill()`: Fills the area enclosed by the path with the current fill style.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/MWNjazP] 

**Bezier Curves**

---

* **Definition**: A Bezier curve is a smooth curve defined by four points: a starting point, an ending point, and two control points.
    
* **How It Works**:
    
    * The control points determine the shape of the curve.
        
    * Imagine pulling a string from the start to the end point, with the control points acting like hands that pull the string to shape it.
        

**Quadratic Curves**

---

* **Definition**: A quadratic curve is similar to a Bezier curve but simpler. It has a starting point, an ending point, and only one control point.
    
* **How It Works**:
    
    * The single control point shapes the curve.
        
    * Think of it as a string pulled from the start to the end point, with one hand (control point) shaping the curve.
        

**Drawing These Curves**

1. **Bezier Curve**:
    
    * Use `moveTo(x, y)` to move the pen to the starting point.
        
    * Use `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, endX, endY)` to draw the curve with two control points.
        
2. **Quadratic Curve**:
    
    * Use `moveTo(x, y)` to move the pen to the starting point.
        
    * Use `quadraticCurveTo(cpx, cpy, endX, endY)` to draw the curve with one control point.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/ExqgPKa] 

### **Drawing Text**

---

1. **Basics of Drawing Text**:
    
    * **Text Functions**:
        
        * `fillText(text, x, y, [maxWidth])`: Draws filled text at the specified (x, y) position.
            
        * `strokeText(text, x, y, [maxWidth])`: Draws text with an outline (stroke) at the specified (x, y) position.
            
    * **Text Measurement**:
        
        * `measureText(text)`: Returns the width of the specified text using the current font settings.
            
2. **Text Properties**
    
    * **Font**:
        
        * Set using `ctx.font = "25px Georgia"`. This is similar to setting font properties in CSS.
            
    * **Text Alignment**:
        
        * `ctx.textAlign`: Aligns text relative to the (x, y) position. Options include `start`, `end`, `left`, `right`, and `center`.
            
    * **Text Baseline**:
        
        * `ctx.textBaseline`: Sets the baseline alignment of the text. Options include `top`, `hanging`, `middle`, `alphabetic`, `ideographic`, and `bottom`.
            
3. **Drawing and Styling Text**
    
    * **Fill and Stroke Styles**:
        
        * Use `ctx.fillStyle` to set the color for filled text.
            
        * Use `ctx.strokeStyle` to set the color for stroked text.
            
4. **Accessibility Considerations**
    
    * **Screen Readers**: Text drawn on the canvas is not accessible to screen readers. Avoid using canvas text as a replacement for regular HTML text elements like `<h1>` or `<p>`.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/wvVzMoX] 

### Drawing Shadows

* **Shadow Properties**: The canvas drawing context has four properties for shadows: `shadowColor`, `shadowOffsetX`, `shadowOffsetY`, and `shadowBlur`.
    
* **Drawing Shadows**: Shadows can be applied to various drawing operations like paths, images, text, and lines. You can control the color, offset, and blur of the shadows.
    
* **Practical Examples**: The video demonstrates how to draw shadows for rectangles, text, and lines, showing how different shadow settings affect the appearance.
    

Example :

%[https://codepen.io/Annamalai-Palani/pen/OJKpLZo] 

### Drawing patterns

---

* **Creating Patterns**: Patterns can be created from images, video frames, or even another canvas element using the `createPattern` function.
    
* **Pattern Repetition**: Patterns can be set to repeat in the x-axis, y-axis, or both.
    
* **Practical Examples**: The video demonstrates creating patterns from an image, a video frame, and another canvas, showing how to apply these patterns to fill or stroke shapes on the canvas.
    

%[https://codepen.io/Annamalai-Palani/pen/YzmZKjY] 

### Drawing gradients

---

Types of Gradients

1. **Linear Gradients**:
    
    * Defined along a straight path between two points.
        
    * You specify the starting and ending points (e.g., from `(x0, y0)` to `(x1, y1)`).
        
    * Colors transition smoothly along this line.
        
2. **Radial Gradients**:
    
    * Defined by two circles: a starting circle and an ending circle.
        
    * The gradient transitions from the edge of the inner circle to the edge of the outer circle.
        
    * You specify the center and radius for both circles.
        

Steps to Create a Gradient

1. **Create the Gradient**:
    
    * Use `createLinearGradient(x0, y0, x1, y1)` for linear gradients.
        
    * Use `createRadialGradient(x0, y0, r0, x1, y1, r1)` for radial gradients.
        
2. **Add Color Stops**:
    
    * Use `addColorStop(position, color)` to define colors at specific points.
        
    * The `position` is a floating-point number between `0` and `1`, representing the percentage along the gradient line or circle.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/XWvMrxd] 

### Drawing Images and Videos on Canvas

---

1. **Source of Images and Videos**:
    
    * You can draw content from an image element, a video element, or another canvas.
        
2. **Using** `drawImage` Function:
    
    * **Basic Usage**:javascriptctx.drawImage(source, x, y);
        
        * Draws the source image/video at the specified `(x, y)` position on the canvas.
            
    * **Scaling the Image**:javascriptctx.drawImage(source, x, y, width, height);
        
        * Draws and scales the source to fit within the specified `width` and `height`.
            
    * **Cropping the Image**:javascriptctx.drawImage(source, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight);
        
        * Draws a portion of the source image defined by `(sx, sy, sWidth, sHeight)` onto the destination canvas at `(dx, dy)` with the size `(dWidth, dHeight)`.
            

### Clipping Paths

---

* **What is a Clipping Path?**
    
    * Think of a clipping path like a mask. It defines an area where drawing can happen. Anything drawn outside this area won't be visible.
        
* **Default Behavior**:
    
    * By default, the entire canvas is the clipping path, meaning you can draw anywhere on it.
        
* **Creating a Clipping Path**:
    
    1. **Draw a Path**: First, you draw a shape (like a circle or a trapezoid).
        
    2. **Apply the Clip**: Use the `clip` function to make this shape the new clipping path.
        

### Using translate

---

* **What is Translate?**
    
    * Translate is like moving a piece of paper around on your desk. It shifts the starting point (origin) of where you draw on the canvas.
        
* **How It Works**:
    
    * Imagine your canvas has a starting point at the top-left corner (0, 0).
        
    * Using the `translate` function, you can move this starting point to a new location.
        
    * For example, if you translate by `(50, 50)`, the new starting point becomes 50 pixels right and 50 pixels down from the original.
        
* **Why Use It?**
    
    * It helps when you have multiple objects to draw, especially if they need to be rotated or scaled. Moving the origin to each object's location can make drawing easier.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/xxvqKBd] 

### Scaling Transformation

---

**What is Scaling?**

* Scaling changes the size of your drawings on the canvas. It multiplies the dimensions of shapes by a scale factor.
    
* For example, if you scale by a factor of 2, a shape will be twice as large. If you scale by 0.5, it will be half the size.
    

Example :

%[https://codepen.io/Annamalai-Palani/pen/NWQpKJV] 

### Using Rotation

---

1. **Rotation in Radians**:
    
    * The canvas uses radians, not degrees, for rotation.
        
    * **Conversion**: To convert degrees to radians, use the formula: `radians = degrees * (Math.PI / 180)`.
        
2. **Rotation Around the Origin**:
    
    * By default, rotation happens around the canvas's origin (top-left corner).
        
    * If you rotate a shape, it will rotate around this point unless you change the origin.
        
3. **Using** `rotate` Function:
    
    * The `rotate` function takes one argument: the angle in radians.
        

Example :

%[https://codepen.io/Annamalai-Palani/pen/dyxvbEJ] 

### Custom transformations

---

* **Custom Transformation Matrices**:
    
    * Custom transforms are defined using a matrix of six values.
        
    * These matrices allow you to create transformations not built into the canvas, like skewing.
        
* **Transform vs. SetTransform**:
    
    * `transform()`: Adds the custom transform to the current canvas transform.
        
    * `setTransform()`: Resets the canvas to the identity transform before applying the custom transform.
        
* **Practical Examples**:
    
    * **Translate**: Recreate the built-in translate function using a custom matrix.
        
    * **Skew**: Create a skew (shear) transform to skew objects along the x or y axis.
        

Example:

%[https://codepen.io/Annamalai-Palani/pen/VwopZJX] 

### Compositing and Global Alpha

---

* **Global Alpha**:
    
    * Controls the opacity of all drawing operations on the canvas.
        
    * Ranges from 0 (fully transparent) to 1 (fully opaque).
        
* **Compositing Methods**:
    
    * There are 12 different methods that determine how new content interacts with existing content on the canvas.
        
    * **Source-over**: Default method where new content is drawn over existing content.
        
    * **Source-in, Source-out, Source-atop**: Control drawing based on intersections with existing content.
        
    * **Destination-over, Destination-in, Destination-out, Destination-atop**: Similar to source methods but affect existing content differently.
        
    * **Lighter, Darker, Copy, XOR**: Apply various effects like lightening, darkening, or exclusive OR operations.
        

Learning HTML Canvas has been an exciting journey, transforming the way I approach software development and design. From the basics of drawing shapes and paths to exploring the more advanced concepts of transformations and compositing, this course has given me the confidence to incorporate more dynamic and visually appealing content into my web projects. Whether you're building games, interactive graphics, or data visualizations, HTML Canvas is an essential tool to have in your developer toolkit. I’m excited to continue experimenting with these techniques and to see how far I can push the limits of what’s possible with canvas. Stay tuned for more projects and insights!