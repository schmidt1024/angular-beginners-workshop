# Angular Beginners Workshop

Angular is a Open Source Framework developed by Google. It is one of the most popular JavaScript Frameworks. Its best use for complex components or whole applications and very well documented. You can convince yourself and read [the official documentation of Angular](https://angular.io/docs) and start with [the Hero tutorial](https://angular.io/tutorial).

In this workshop we are building a movie app step by step. It is a pratical entry into programmering Angular with TypeScript. Basic know how in JavaScript, HTML and CSS will help you to understand TypeScript, Templating and SCSS.

## Developing

We are using [StackBlitz](https://stackblitz.com/) for online coding our example movie app. There will be a box for every step, so you can dive in any time after loosing your code with the example one. This is a good way for practising coding. Of course you can setup a local environment.

### StackBlitz

As entry point there is [Angular Beginners Workshop (ABW) Starter App][00] available online under StackBlitz.

[![StackBlitz Angular Beginners Workshop (ABW) Starter App][02]][00]

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

## Basics

Inside the Angular project you find a bundle of folders and files. The goal is not to explain every file. We just want to dive in developing mode and only take these files, which are neccessary for us to dive into coding.


```
...
src
    app
        app.component.css
        app.component.html
        app.component.spec.ts
        app.component.ts
        app.module.ts
    ...
    index.html
    ...
```

Angular allows us to build single page applications. The file index.html is the single page. Take a look at it.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>ABW Start</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>
```

Here we define a `<title>` we can see on the browsers tab. The body of the file is interesting. We see the `<app-root>` element in there. But if we look at the browser a different content will be displayed: A 'Welcome' message and the Angular logo. So something must be change here. Well, the `<app-root>` element is not a default html element. Instead it is one of our own components. By installing a new Angular app through CLI (or cloning this example app), Angular comes with root component. Every file in the folder `src` which starts with `app.component...` belongs to this root component.

Now take a look at the file `app.component.ts`.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular';
}
```

Here we find the `@Component` decorator and in there is the `selector` property, which has `app-root` as string. This is the information that Angular need to replace the `<app-root>` element from the `index.html` with the template of this component. The template of this component is in file `app.component.html`.

```html
<!--The content below is only a placeholder and can be replaced.-->
<div style="text-align:center">
  <h1>
    Welcome to {{ title }}
  </h1>
  <img width="240" alt="Angular Logo" src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg==">
</div>
```

This is basically what happens at the startup.

> Decorators are functions that modify JavaScript classes. Angular defines a number of decorators that attach specific kinds of metadata to classes, so that the system knows what those classes mean and how they should work. 
> 
> Source: [Angular - Architecture overview][101]
> 
> [Learn more about decorators on the web][102].

## Practice

[Build a simple movie app][01].

Tasks

- [ ] Add a `title` and an `image` for one movie
- [ ] List the movie in your template three times

Notes

- You can use [https://via.placeholder.com/240x360](https://via.placeholder.com/240x360) for the image src

Hints

- An unsorted list `<ul>` is a good choice
- Take a helper array, e.g. `num = [1, 2, 3]`
- Iterate on the list item with `*ngFor="let i of num"`

Style

For a better result you can style the output in file `app.component.css`.

```css
ul {
    list-style: none;
    margin: 0;
    padding: 0;
}
```

A simple reset for unsorted lists.

## Service

For our movie app we want to get data from an extern source. themoviedb.org offers an public api, where we can fetch a json with film results. To fetch it in Angular we create a service. Services are a great way to share information between components that don't know each other.

## Practice

[Create a movie service][02].

Tasks

- [ ] Create in new file `movie.service.ts`
- [ ] Setup the `HttpClient`
- [ ] Subscribe to the service

Notes

- Use [https://api.themoviedb.org/3/movie/top_rated?api_key=d7fc424ee402bd0666f5f420c5201966&page=1&region=CH](https://api.themoviedb.org/3/movie/top_rated?api_key=d7fc424ee402bd0666f5f420c5201966&page=1&region=CH) as given api url

Hints

Create a new file `movie.service.ts` in folder `app` with the following basic content.

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class MovieService {

  constructor() { }
}
```

Or use the cli if you work local.

```console
ng generate service movie --skipTests=true
```

If you use this command without the flag `--skipTests=true` it will generate additionally the file `movie.service.spec.ts` for testing purpose. Testing is no topic of this workshop. So we can delete or simply ignore this file if generated.

### HttpClient

Before you can use the `HttpClient` to get data from a specific url, you need to import the `HttpClientModule` in file `app.module.ts`. 

```typescript
import { HttpClientModule } from '@angular/common/http';
```

Now you can inject the `HttpClient` in your `movie.service.ts`.

```typescript
import { HttpClient } from '@angular/common/http';
```

Additionally make it available in your class.

```typescript
constructor(
  private http: HttpClient
) { }
```

Now you can provide a subscription of data in a function for later use in your component.

```typescript
getMovies() {
  return this.http.get('https://api.themoviedb.org/3/movie/top_rated?api_key=d7fc424ee402bd0666f5f420c5201966&page=1&region=CH');
}
```

For a better readability you should outsource the url in a `const`.

> Excursion: Angular offers environments for development and production. It is possible to have different api urls for the different modes (prod or dev). Therefore you should define the urls in the files provided for. You find them in folder `environments` in you `src` directory. After the property `production` you can define a new property `apiUrl` with the url as value. Then you `import { environment } from '../environments/environment'` in your service and define `const apiUrl = environment.apiUrl` to work with. 

### Subscribe

It's time to `subscribe` to the service to get the data. To do so inject your the movie service in your `app.component.ts`.

```typescript
import { MovieService } from './movie.service';
```

Inside the constructor you have access to the service. Time to code the function to subscribe to.

```typescript
constructor(
  private movieService: MovieService
){
  this.movieService.getMovies()
  .subscribe(data => {
    console.log(data);
  });
}
```

After refresh your app in the browser you should see the data in the console. Well done!

... to be continued ...

[//]: # (app links)
[00]: https://stackblitz.com/github/Bloggerschmidt/abw-start/ "StackBlitz Angular Beginners Workshop (ABW) Starter App"
[01]: https://stackblitz.com/github/Bloggerschmidt/abw-s01 "ABW Movie App Version 1"
[02]: https://stackblitz.com/github/Bloggerschmidt/abw-s02 "ABW Movie App Version 2"
[03]: https://stackblitz.com/github/Bloggerschmidt/abw-s03 "ABW Movie App Version 3"

[//]: # (reference links)
[101]: https://angular.io/guide/architecture "Angular - Architecture overview"
[102]: https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841 "Exploring EcmaScript Decorators"
[103]: https://angular.io/guide/observables "Angular Official Documentation - Observables"

[//]: # (image links)
[1001]: images/stackblitz.com-abw-start.png "Screenshot StackBlitz Angular beginners workshop starter app"
