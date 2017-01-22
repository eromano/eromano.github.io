---
layout: post
comments: true
truncate: 150
lang: it
title: Angular 2 3D Viewer
---
Negli ultimi 2 anni Angular2 ha preso sempre piu' spazio nella mia vita, fortunatamente dalle sofferenze delle beta versions alle ultime final release il framework ha iniziato a consolidarsi e a dare molti meno grattacapi e piu' soddisfazioni.

Secondo il mio parere uno dei punti di forza di Angular2 in questo momento e' la modularita' ed e' proprio seguendo questa filosofia dei componenti che nelle ultime due settimane ho **creato un componente che permette la renderizzazione di oggetti 3D in un browser.**

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

Prima di dilungarmi in spiegazioni tecniche su come usare questo componente, ecco qualche utile scorciatoia:

* Link github al progetto: [Angular2 3D editor](https://github.com/eromano/ng2-3d-editor)
* Link di un piccolo esempio in cui trovate il codice e la demo: [Plunkr example Angular 2 3D editor](https://plnkr.co/edit/I4lIyA?p=preview)
* Link npm per scaricarlo da npm: [Npm page](https://www.google.co.uk/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=ng2%203d%20editor%20npm)

# How it works

Per effettuare la renderizzazione dei files 3D ng2-3d-editor utilizza la libreria [three.js](https://threejs.org) di cui potete trovare [documentazione](https://threejs.org/docs/index.html#Manual/Introduction/Creating_a_scene) ed [esempi](https://threejs.org/examples/) a questi links.

# Code

Ecco in breve un piccolo snippet di codice su come utilizzare questo componente anyway per una soluzione piu' completa vi suggerisco di utilizzare il codice presente nel [Plunkr example online](https://plnkr.co/edit/I4lIyA?p=preview):

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

Le opzioni di personalizzazione del **threed-viewer** che al momento e' tutto quello che c'e' da aggiungere nell'HTML sono le seguenti:

Attribute     | Options     | Default      | Description | Mandatory
---           | ---         | ---          | ---         | ---
`urlFile`         | *string*    |        |  Url 3D file to load |
`initialPositionCamera`         | *Object*    |        |   If you want change  the initial camera position pass an object {x:xvalue , y:yvalue , z:zvalue}|
`initialRotationCamera`         | *Object*    |        |   If you want change  the initial camera rotation  pass an object {x:xvalue , y:yvalue , z:zvalue}|
`clearColor`         | *Hexadecimal color*    |        |   Sets the clear color |


# Considerazioni Finali

Per il capitolo prossimi sviluppi **al momento questo componente visualizza solo file di formato OBJ** ma rendero' possibile nei prossimi giorni anche la visualizzazione di altri formati 3D come 3DS per gli amanti di 3DSMax.

Per chiunque abbia voglia di partecipare con me nello sviluppo di questo simpatico componente le porte sono aperte, mandatemi una mail o un piccione viaggiatore se preferite.
