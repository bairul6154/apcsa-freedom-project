# Entry 4
##### 2/9/20

# Abstract
I have finally figured out how to create animations and a bit of interactivity using Babylon.

---
# Engineering Design Process
I am still **researching** and **brainstorming** how to use Babylon to create my product. However, I don't want to take too long in the researching
and learning process because surely there is no way I can learn everything about Babylon with limited time. I am learning what
I needed to use in my product to save time. Those include interactivity and animations which I learned in the past weeks.

### Animation
A quick vocabs:

A ***Mesh*** is used as the NAME of a SHAPE that is computer generated in 3D space<br>
***Mesh Property*** is what defines a mesh. Possible proprties include:
* rotation (ex. `rotation.x += 10`)
* position (ex. `position.y -= 5`)
* material (this is the color property.)


The first way I learned about animation is using *key frames* just like in **CSS**.
This is a [copy](https://jsbin.com/femiciwicu/edit?html,css,js,output) of the code below.

```javascript
//This declaration creates a new FORM of animation
var animationName = new BABYLON.Animation("animationName", "rotation.x",
    30, BABYLON.Animation.ANIMATIONTYPE_FLOAT, BABYLON.Animation.ANIMATIONLOOPMODE_CYCLE);

//------------------------------------------------------------------------------------
//This creates an array that can be filled with frames of the animation just like CSS
var keyFrames = [];
//Parameters {frame number, the value of the Mesh Property that's changing}
keyFrames.push({frame:0, value:0});
keyFrames.push({frame:100, value: 5});
animationName.setKeys(keyFrames); //This line BINDS the keys the new animation created
//------------------------------------------------------------------------------------

mesh.animations = [];
//BINDING the mesh of your choice to the newly created animation
mesh.animations.push(animationName);
scene.beginAnimation(mesh, 0, 100, true); //starting the animation
//Parameters {name of mesh, start frame number, end frame number}
```

More on what each parameter does on the [tutorial](https://doc.babylonjs.com/babylon101/animations). There are many other ways to
create animations. In this [example](https://www.babylonjs-playground.com/#J19GYK#0) that the tutorial gave us, the animation for the
donut ring - if you scroll all the way to the bottom - were created in a way without the key frames.


### Interactivity
There are numerous ways to add interactivity. The most simplest way to create something called *Actions*. There are two steps
to actions: 1, create a action for a mesh. 2, create a registerAction which is the TYPE of action, HOW will the action be
triggered, and WHAT will happen to the mesh.
```javascript
//Creates a action to a mesh
mesh.actionManager = new BABYLON.ActionManager(scene);

//Parameters for{trigger, target, propertyPath, value}
mesh.actionManager.registerAction(new BABYLON.SetValueAction(BABYLON.ActionManager.OnPointerOverTrigger
    , box, "scaling", new BABYLON.Vector3(2,2,2)));
//                                                                                  ^over the mesh
//                                                                                  v not over the mesh
mesh.actionManager.registerAction(new BABYLON.SetValueAction(BABYLON.ActionManager.OnPointerOutTrigger,
    box, "scaling", new BABYLON.Vector3(1,1,1)));
```
This [action](https://jsbin.com/xenicesoci/edit?html,css,js,output) makes the mesh increase in size when the mouse is hovering over it.

By changing the `SetValueAction` to `InterpolateValueAction`, it becomes a animation

```javascript
box.actionManager = new BABYLON.ActionManager(scene);

box.actionManager.registerAction(new BABYLON.InterpolateValueAction(
    BABYLON.ActionManager.OnPointerOutTrigger,box, "scaling", new BABYLON.Vector3(1, 1, 1),500));
//                                                          this is the animation duration^
//                                                          (ex. 1000 is 1 second)
box.actionManager.registerAction(new BABYLON.InterpolateValueAction(
    BABYLON.ActionManager.OnPointerOverTrigger, box, "scaling", new BABYLON.Vector3(2, 2, 2),500));
```
[See](https://jsbin.com/dumavefuma/edit?html,css,js,output) the difference between just setting the values to interpolating the values

I plan on using these animation and actions to create a 3D molecule model that users can click or hover on.

---
# Skills
I am able to develop my **how to learn** skills because more often than not, I don't understand the wording of the tutorial.
As my last resort, I use the examples that the tutorial gives us to learn on my own. First, I create a new test.html and then
copy and paste codes that I want to learn from the example. Finally, I tinker around with the parameters and retype the code using my
objects to help me understand better.

---
# Knowledge
I noticed that there are a lot of `new` which is a instantiation like **Java** which we are learning in school. As a result,
I am able to understand what's going on behind the scene of Babylon.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)