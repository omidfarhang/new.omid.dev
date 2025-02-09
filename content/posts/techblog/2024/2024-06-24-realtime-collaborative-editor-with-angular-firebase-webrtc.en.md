---
title: 'Building a Real-Time Collaborative Editor with Angular, Firebase, and WebRTC: A Step-by-Step Guide'
date: 2024-06-24T02:03:44+03:30
layout: single
author_profile: true
url: 2024/06/24/realtime-collaborative-editor-with-angular-firebase-webrtc/
shortlink: https://g.omid.dev/B5GbSr0
tags:
  - Angular
  - Frontend Development
  - Firebase
  - WebRTC
  - Real-Time App
lang: en
categories: 
  - TechBlog
---
Creating a real-time collaborative text editor can be a challenging but rewarding project. In this guide, we'll walk you through the process of building a real-time collaborative editor using Angular, Firebase, and WebRTC. By the end of this tutorial, you’ll have a working understanding of these technologies and how to integrate them to create a seamless, real-time collaborative experience.

## Introduction

Real-time collaborative applications are increasingly popular in today's digital world. They allow multiple users to work on the same document simultaneously, seeing each other's changes in real time. Google Docs is a prime example of such an application. In this tutorial, we will build a similar application using modern web technologies.

## Prerequisites

Before we start, make sure you have the following installed:

- Node.js and npm
- Angular CLI
- Firebase account
- Basic knowledge of Angular and TypeScript

## Setting Up the Angular Project

First, let’s set up a new Angular project. Open your terminal and run:

```bash
ng new collaborative-editor
cd collaborative-editor
ng serve
```

This will create a new Angular project and start a development server. Open your browser and navigate to `http://localhost:4200` to see your new Angular application.

## Integrating Firebase

Firebase provides a powerful backend as a service, which is perfect for building real-time applications. We will use Firebase Firestore for real-time database functionality and Firebase Authentication for user management.

### Setting Up Firebase

1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Create a new project.
3. Add a web app to your project.
4. Copy the Firebase configuration details.

### Installing Firebase

In your Angular project, install Firebase and AngularFire:

```bash
npm install firebase @angular/fire
```

### Configuring Firebase

Open `src/environments/environment.ts` and add your Firebase configuration:

```typescript
export const environment = {
  production: false,
  firebase: {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID",
    measurementId: "YOUR_MEASUREMENT_ID"
  }
};
```

### Initializing Firebase in Angular

In `src/app/app.module.ts`, import and initialize AngularFire:

```typescript
import { AngularFireModule } from '@angular/fire';
import { AngularFirestoreModule } from '@angular/fire/firestore';
import { AngularFireAuthModule } from '@angular/fire/auth';
import { environment } from '../environments/environment';

@NgModule({
  declarations: [
    // Your components
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    AngularFireModule.initializeApp(environment.firebase),
    AngularFirestoreModule,
    AngularFireAuthModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

## Setting Up WebRTC

WebRTC (Web Real-Time Communication) enables peer-to-peer communication in web applications. We'll use it to handle real-time data exchange between clients.

### Installing WebRTC

WebRTC is a native browser API, so you don't need to install any additional packages. However, we will use simple-peer, a lightweight wrapper around WebRTC, to simplify the implementation.

Install simple-peer:

```bash
npm install simple-peer
```

### Creating the WebRTC Service

Create a service to manage WebRTC connections. Run:

```bash
ng generate service webrtc
```

In `src/app/webrtc.service.ts`, implement the WebRTC functionality:

```typescript
import { Injectable } from '@angular/core';
import * as SimplePeer from 'simple-peer';

@Injectable({
  providedIn: 'root'
})
export class WebrtcService {
  peers: { [key: string]: SimplePeer.Instance } = {};

  constructor() {}

  createPeer(isInitiator: boolean, stream: MediaStream, signalCallback: (data: any) => void): SimplePeer.Instance {
    const peer = new SimplePeer({
      initiator: isInitiator,
      stream: stream,
      trickle: false
    });

    peer.on('signal', signalCallback);

    peer.on('error', err => {
      console.error('Peer error:', err);
    });

    return peer;
  }

  connectPeer(peer: SimplePeer.Instance, signal: any): void {
    peer.signal(signal);
  }
}
```

## Building the Text Editor Component

Now, let's create the text editor component. We'll use Angular's `FormControl` to manage the text input and bind it to the Firebase database.

### Generating the Component

Run:

```bash
ng generate component text-editor
```

### Implementing the Text Editor

In `src/app/text-editor/text-editor.component.ts`:

```typescript
import { Component, OnInit } from '@angular/core';
import { FormControl } from '@angular/forms';
import { AngularFirestore } from '@angular/fire/firestore';
import { AuthService } from '../auth.service';
import { WebrtcService } from '../webrtc.service';

@Component({
  selector: 'app-text-editor',
  templateUrl: './text-editor.component.html',
  styleUrls: ['./text-editor.component.css']
})
export class TextEditorComponent implements OnInit {
  editorControl = new FormControl('');
  docId = 'collaborative-doc';

  constructor(
    private firestore: AngularFirestore,
    private authService: AuthService,
    private webrtcService: WebrtcService
  ) {}

  ngOnInit(): void {
    this.firestore.collection('documents').doc(this.docId).valueChanges().subscribe((doc: any) => {
      if (doc) {
        this.editorControl.setValue(doc.content, { emitEvent: false });
      }
    });

    this.editorControl.valueChanges.subscribe(content => {
      this.firestore.collection('documents').doc(this.docId).set({ content }, { merge: true });
    });

    // Add WebRTC setup code here
  }
}
```

In `src/app/text-editor/text-editor.component.html`:

```html
<textarea [formControl]="editorControl" rows="10" cols="50"></textarea>
```

## Real-Time Collaboration with Firebase

We’ve set up Firebase and our text editor component. Now, let's ensure real-time updates are reflected for all users.

### Listening for Document Changes

We already have the Firebase document listener in place. This will update the editor whenever the document changes in the database.

### Updating the Document

We also have the document update logic in place. Whenever the editor content changes, it updates the document in Firebase.

## Adding WebRTC for Peer-to-Peer Communication

WebRTC will handle the direct communication between clients for real-time updates, minimizing latency and offloading the server.

### Setting Up the Peer Connections

In `src/app/text-editor/text-editor.component.ts`, update the `ngOnInit` method:

```typescript
ngOnInit(): void {
  // Existing Firebase logic...

  this.authService.user$.subscribe(user => {
    if (user) {
      const peer = this.webrtcService.createPeer(true, null, signal => {
        // Send signal to Firebase or other signaling server
      });

      // Listen for signals from other peers
      this.firestore.collection('signals').doc(user.uid).valueChanges().subscribe((signal: any) => {
        if (signal) {
          this.webrtcService.connectPeer(peer, signal);
        }
      });
    }
  });
}
```

## Deploying the Application

To deploy our application, we'll use Firebase Hosting.

### Installing Firebase Tools

If you haven't already, install Firebase Tools:

```bash
npm install -g firebase-tools
```

### Initializing Firebase Hosting

Run:

```bash
firebase login
firebase init
```

Choose Hosting and follow the prompts to set up Firebase Hosting in your project.

### Deploying

Build and deploy your project:

```bash
ng build --prod
firebase deploy
```

## References

- [Angular Documentation](https://angular.dev)
- [Firebase Documentation](https://firebase.google.com/docs)
- [WebRTC API](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API)
- [simple-peer GitHub](https://github.com/feross/simple-peer)

## Conclusion

Congratulations! You've built a real-time collaborative text editor using Angular, Firebase, and WebRTC. This application allows multiple users to edit the same document simultaneously, with changes being reflected in real-time. By leveraging Firebase for backend services and WebRTC for peer-to-peer communication, you’ve created a robust and scalable collaborative tool.
