# Angular Beginners Workshop

Angular is a Open Source Framework developed by Google. It is one of the most popular JavaScript Frameworks. Its best use for complex components or whole applications and very well documented. You can convince yourself and read [the official documentation of Angular](https://angular.io/docs) and start with [the Hero tutorial](https://angular.io/tutorial).

In this workshop we are building a movie app step by step. It is a pratical entry into programmering Angular with TypeScript. Basic know how in JavaScript, HTML and CSS will help you to understand TypeScript, Templating and SCSS.

## Developing

We are using [StackBlitz][01] for online coding our example movie app. There will be a box for every step, so you can dive in any time after loosing your code with the example one. This is a good way for practising coding. Of course you can setup a local environment.

### StackBlitz

As entry point there is [Angular starter app][01] available online under StackBlitz.

[![StackBlitz Angular beginners workshop starter app][02]][01]

Be patient! Starting a dev server under StackBlitz.com could take a while.

### Local

Setup your local environment by installing [Node.js](https://nodejs.org), your favorite IDE ([VSCode](https://code.visualstudio.com/), [WebStorm](https://www.jetbrains.com/webstorm/), [Sublime Text](https://www.sublimetext.com/), etc [...](https://twitter.com/iamdevloper/status/1101107279019929600?lang=en)) and [Angular CLI](https://cli.angular.io). By installing Node.js you installed the package manager `npm` as well. With it you can install globally the Angular CLI with following command.

```console 
npm install -g @angular/cli
```

With Angular CLI it is very handy to start a new app.

```console 
ng new abw-app
cd abw-app
ng serve
```

You can also clone the repository with git.

```console 
git clone git@git.namics.com:alschmidt1/abw-start.git
````

or

```console 
git clone git@github.com:Bloggerschmidt/abw-start.git
```

Starting the app with

```console
ng serve
```

Open your browser on [http://localhost:4200](http://localhost:4200/).


[01]: https://stackblitz.com/github/Bloggerschmidt/abw-start/ "StackBlitz Angular beginners workshop starter app"
[02]: images/stackblitz.com-abw-start.png "Screenshot StackBlitz Angular beginners workshop starter app"

