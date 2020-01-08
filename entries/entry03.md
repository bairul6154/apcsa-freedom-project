# Entry 3
##### 1/6/2020

# Abstract
I am still continuing with my journey in learning and exploring the basics of Babylon.js and what it have in store for me.
I have tried to brainstorom ideas on what the product will look like.

---
# Knowledge

From my Junior year in the SEP, I have learned the basics of **HTML**, **CSS**, and **JS**; as a result, I have a better time understanding the code since Babylon.js is
web based and these front end languages. Addtionally, from my Sophomore year I learned about a 2D JavaScript engine called **p5js** which is similar to Babylon in a way.


---
# Engineering Design Process
From my previous blog entry, I mentioned that I am tinkering with the [template](https://jsbin.com/hepetukemu/edit?html,css,output) to try and figure out what individual line of code do.
I have documented my findings on a Google Doc; here are some of the important must have **JavaScript** codes in order to function:

* Gets the `<canvas>` element from the HTML
   ```javascript
   var canvas = document.getElementById("renderCanvas");
   ```
* This code gets the `<canvas>` ready for Babylon codes; this is similar to git init
   ```javascript
   var engine = new BABYLON.Engine(canvas, true);
   ```

Some basic shapes inside the `createScene` function; basically everything you want on the screen goes in `createScene`
* Generates a cube or any other cuboid. In **p5js** terms, this is similar to `rect();`
   ```javascript
   var boxName = BABYLON.MeshBuilder.CreateBox("boxName", {width: 2, height, 3, depth: 2}, scene);
   ```
* Generates a sphere or any other ellipsoid. Similar to `ellipse();` in **p5js**
   ```javascript
   var sphereName = BABYLON.MeshBuilder.CreateSphere("sphereName", {diameter: 1.25}, scene);
   ```

---
# Skills

By breaking down code to understand them, I was able to work on my **problem solving** skills. Staring at a big chunk of code is like confronting the final boss in a dungean.
However, by chipping away at the code one piece at a time, I am able to understand the code faster and better.

---
# Next Steps
I want to get through the [tutorial](https://doc.babylonjs.com/babylon101/) as soon as possible; right now I am at the step of creating animations.

I have looked at other cool things that Babylon can offer:
* [GUI](https://www.babylonjs.com/demos/gui/)s (graphical user interface) are peppermint
* Using [Actions](https://www.babylonjs-playground.com/#J19GYK#0) AKA interactivity

I also need to sit down with my Chemistry teacher and have a quick refresher to jog my memory.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)