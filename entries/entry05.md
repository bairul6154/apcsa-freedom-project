# Entry 5
##### 3/15/20

# Abstract
I have been planning what my final project is going to be like. I also learnt about using instances in Babylon in the process.

---
# Engineering Design Process
I have looked back at my [old project](https://bairul6154.github.io/ChemProject/) and see what else I can do to make it better besides scaling it up to 3 dimensions.
I realized that I won't be able to remake it into a game with the time I have left; therefore, I will just make it a simulation like
a sandbox for users to mess around with.

My other idea is instead of using the keyboard to change electron geometry, I will be using the mouse to click on  Graphical User Interfaces (GUI)
and on the molecular model itself. I feel that this way will be a lot simpler for people to understand and use this product. When I was
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
What this code does is when a mesh, in this case sp1)  disappear the sphere and then


---
[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)