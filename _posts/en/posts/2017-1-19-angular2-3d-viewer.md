---
layout: post
comments: true
truncate: 150
title: Angular 2 3D Viewer
---
Angular2 during the last 2 years has become more important in my life as a developer, fortunately from the sufferings of the beta versions to the latest final release, the framework has started to consolidate and give less trouble and more satisfaction.

In my opinion, one of the strengths of Angular2 nowadays is the 'modularity'. Following this component philosophy, in the last two weeks, I ** have created a new component that enables you to render 3D objects in a browser. **

<div id="gallery">
    <h2>Angular 2 3D Viewer</h2>
    <div class="row">
        <article class="6u 12u$(xsmall) work-item">
            <a href="/images/ng2-3d-editor/ScreenShot1.png" class="image fit thumb"><img src="/images/ng2-3d-editor/ScreenShot1.png" alt="3d viewer angular 2" /></a>
        </article>
            <article class="6u 12u$(xsmall) work-item">
                <a href="/images/ng2-3d-editor/ScreenShot2.png" class="image fit thumb"><img src="/images/ng2-3d-editor/ScreenShot2.png" alt="3d viewer angular 2" /></a>
            </article>
        </div>
</div>

Before dwell on technical explanations of how to use this component, here is some useful shortcut:

* Link to the github project: [3D Angular2 editor] (https://github.com/eromano/ng2-3d-editor)
* Link to a small example where you can find the code and demo: [Plunkr example Angular 2 3D editor] (https://plnkr.co/edit/I4lIyA?p=preview)
* Link to download it from NPM: [Npm page] (https://www.google.co.uk/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=ng2%203d%20editor%20npm )

# How it works

In order to render a 3D file the ng2-3d-editor component use the library [Three.js] (https://threejs.org) of which you can find [documentation] (https://threejs.org/docs/index.html # Manual / Introduction / Creating_a_scene) and [examples] (https://threejs.org/examples/) to these links.

# Code

Above you can find a small snippet of code on how to use this component, anyway for a complete solution I suggest you to use the code inside the [Plunkr online example] (https://plnkr.co/edit/I4lIyA?p=preview) :

```javascript
//our root app component
import { Component, NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { Editor3DModule } from 'ng2-3d-editor';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'my-app',
  template: `
     <threed-viewer [initialRotationCamera]="initialRotationCamera" [initialPositionCamera]="initialPositionCamera" [urlFile]="urlFile" [clearColor]="clearColor"></threed-viewer>
  `,
})
export class App {
  initialPositionCamera:any;
  initialRotationCamera:any;
  urlFile:string = 'https://cdn.rawgit.com/eromano/ng2-3d-editor/master/examples/obj/car/car.obj';

  clearColor:any;

  constructor() {
   this.initialRotationCamera = {x: -0.3569454377164346, y: 0.8226385481329694, z: 0.2668119404891661};
   this.initialPositionCamera =  {x: 14.95050234828009, y: 4.848633256815587, z: 13.0018215134665};
   this.clearColor = 0xf0f0f0;
   console.log('start');
  }
}

@NgModule({
  imports: [
    CommonModule,
    BrowserModule,
    Editor3DModule.forRoot()
  ],
  declarations: [ App ],
  bootstrap: [ App ]
})
export class AppModule {}
```

The customization options  of the ** threed-viewer **  tag  that is all you need to add inside your HTML are the following:

Attribute     | Options     | Default      | Description | Mandatory
---           | ---         | ---          | ---         | ---
`urlFile`         | *string*    |        |  Url 3D file to load |
`initialPositionCamera`         | *Object*    |        |   If you want change  the initial camera position pass an object {x:xvalue , y:yvalue , z:zvalue}|
`initialRotationCamera`         | *Object*    |        |   If you want change  the initial camera rotation  pass an object {x:xvalue , y:yvalue , z:zvalue}|
`clearColor`         | *Hexadecimal color*    |        |   Sets the clear color |


# Final comments

For the chapter next developments ** ng2-3d-editor now is able to render only OBJ file format  ** I will add in the coming days even the possibility to render other 3D formats such as 3DS for the 3DSMax lovers.

For anyone willing to join with me in developing this component the doors are open, or send me an e-mail or a carrier pigeon if you prefer.
