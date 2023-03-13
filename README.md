## Guide to Including an Angular App with Routing in a Web Component


👋 Welcome the guide on how to include an entire Angular app with routing inside a web component!

Introduction
------------

Will be used `@angular/elements` to create a web component in Angular, and the entire app will be included inside it.

Getting Started
---------------

1.  Clone the repository
2.  Install dependencies using `npm install`
3.  Build using `ng build`
4.  Package to compile the `dist/*.*.js` angular build into `angular-in-web-component.js` using `npm run package`
5.  Serve using `npm run serve`

Here are the relevant commands:

```json
"start": "ng serve",
"build": "ng build",
"package": "cat ./dist/angular-in-web-component/{polyfills,runtime,main}.*.js > ./test-angular-web-component/angular-in-web-component.js && cp ./dist/angular-in-web-component/styles.*.css ./test-angular-web-component/styles.css",
"serve": "npx -p http-server http-server ./test-angular-web-component/ -o --cors --port 8080 -P http://localhost:8080?",
```

The `package` command will copy also the generated style file `styles.css` into the `test-angular-web-component` directory.

Here is the file tree:

```
├── angular-in-web-component.js
├── index.html
└── styles.css
```

Guide
-----

### Installation

Install `@angular/elements` with the following command:

`npm i @angular/elements -D`

### AppModule

In `app.module.ts`, use `@angular/elements` to include the `AppComponent` component and define it with `customElements.define`.

**Remember** to set the same selector in `AppComponent` as the one used in `customElements.define`.

Here is the file tree of the app:


```
.
├── app
│   ├── app-routing.module.ts
│   ├── app.component.html
│   ├── app.component.scss
│   ├── app.component.ts
│   ├── app.module.ts
│   └── home
│       ├── container
│       │   ├── home.component.html
│       │   ├── home.component.scss
│       │   └── home.component.ts
│       ├── home-routing.module.ts
│       └── home.module.ts
├── assets
├── favicon.ico
├── index.html
├── main.ts
└── styles.scss
```

### Routing

There is another module inside the app called `home`, which can be accessed at `/home` to test routing.

That's it! You can now include the Angular app with routing inside a web component.

Happy coding! 💻
