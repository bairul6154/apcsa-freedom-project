# Entry 5
##### 3/15/20

# Abstract
I have been planning what my final project is going to be like. I also learnt about using instances in Babylon in the process.

---
# Engineering Design Process
I have looked back at my [old project](https://bairul6154.github.io/ChemProject/) and see what else I can do to make it better besides scaling it up to 3 dimensions.
I realized that I won't be able to remake it into a game with the time I have left; therefore, I will just make it a simulation like
a sandbox for users to mess around with.

My other idea is instead of using the keyboard to change electron geometry, I will be using the mouse to click on Graphical User Interfaces (GUI)
on the side of the screen, and on the molecular model itself. I feel that this way will be a lot *simpler* for people to understand and use this product. When I was
showing off my old project during the presentation last year, I noticed that not many people understand the controls and how to play. What
is the point of anything if nobody (except the creator) knows how to use your product. As a result, using visual controls will be a lot
easier.

I have been messing around with Babylon Actions to recreate what I envisioned in my head:

```javascript
var setSphere = function(mesh) {//creating this action function
    mesh.actionManager = new BABYLON.ActionManager(scene);
    mesh.actionManager.registerAction(new BABYLON.InterpolateValueAction(BABYLON.ActionManager.OnPointerOutTrigger, mesh, "scaling", new BABYLON.Vector3(1, 1, 1), 150));
    mesh.actionManager.registerAction(new BABYLON.InterpolateValueAction(BABYLON.ActionManager.OnPointerOverTrigger, mesh, "scaling", new BABYLON.Vector3(1.2, 1.2, 1.2), 150));

    mesh.actionManager.registerAction(new BABYLON.CombineAction(BABYLON.ActionManager.OnPickTrigger,[
        new BABYLON.SetValueAction(BABYLON.ActionManager.OnPickTrigger,mesh,'visibility',0),
        new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger,
        function(){
            on = true;
        })
    ]))
    .then(new BABYLON.CombineAction(BABYLON.ActionManager.OnPickTrigger,[
        new BABYLON.SetValueAction(BABYLON.ActionManager.OnPickTrigger,mesh,'visibility',1),
        new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger,
        function(){
            on = false;
        })
    ));
}
setSphere(sp1);//calling the action function
```

This chunk of code is just a snippet of the [full code](https://jsbin.com/juborumoya/edit?html,output).
What this function does is when clicked on a mesh, it will change into a cube and vice versa. How I will be using this technique is
to have the user click on the bonded pairs to select and then click on one of the buttons on the GUI to switch it to lone pairs or
vice versa.

The last thing I need to learn is how to make GUIs, but that will be in the next blog entry.

---
# Knowledge
When I was planning and creating a test model, I ran into a problem: *repetition*. I have to wrtie code for each individual mesh on the sceen.
I thought to myself, well this is a pain in the. As a result, I looked into how I can create multiple meshes that are the same more efficiently.

Introducing instances:
```javascript
for (var i=0; i< 10; i++) {
    for (var k=0; k<10; k++) {
        var instance = box.createInstance("box"+i+k);
        instance.position.z+=k*2;
        instance.position.x+=i*2;
        setBox(instance);
    }
}
```
With just *8 lines* of code, I have created [100 boxes](https://jsbin.com/meyurubuja/edit?html,output) at once.

What else uses instances, **Java**. In Java, you can create a class, and then make any number of instances of that class. In Babylon, it is the
same. I have to create a mesh first, and then use that mesh as a *template* to create instances of that same mesh.

---
# Skills
Over the past weeks on this project, I have been working on **consideration** and **time management**. As I have mentioned before, I want to make
this project more easier and simpler to use than my old one. I have to think about how others would use my product and *consider* their actions
and thinking when creating. The due date for the MVP is on April 20. I need to create a product that is not necessarily perfect, but viable
at that point. I have been replanning my ideas and stripping down on things that are *extra* and working towards ideas that *needs* to works first.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)