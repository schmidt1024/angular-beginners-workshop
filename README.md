# Angular Beginners Workshop

Angular is a Open Source Framework developed by Google. It is one of the most popular JavaScript Frameworks. Its best use for complex components or whole applications and very well documented. You can convince yourself and read [the official documentation of Angular](https://angular.io/docs) and start with [the Hero tutorial](https://angular.io/tutorial).

In this workshop you are building a movie app step by step. It is a pratical entry into programmering Angular with TypeScript. Basic know how in JavaScript, HTML and CSS will help you to understand TypeScript and Templating.

## Content

- [Setup](#setup)
- [Basics](#basics)
- [Dependency Injection](#dependency-injection)
- [Services](#services)
- [Templating](#templating)
- [Event binding](#event-binding)
- [$event and event handling](#event-and-event-handling)
- [Stopping propagation](#stopping-propagation)
- [@Input](#input)
- [@Output](#output)
- [EventEmitter](#eventemitter)

## Setup

You are using [StackBlitz](https://stackblitz.com/) for online coding your example movie app. There will be a box for every step, so you can dive in any time after loosing your code with the example one. This is a good way for practising coding. Of course you can setup a local environment.

### StackBlitz

As entry point there is [Angular Beginners Workshop (ABW) Starter App][00] available online under StackBlitz.

[![StackBlitz Angular Beginners Workshop (ABW) Starter App][02]][1001]

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
<!-- index.html -->
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
// app.component.ts
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
<!-- app.component.html -->
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

## 🔥Practice

[Build a simple movie app.][01]

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
/* app.component.css */
ul {
    list-style: none;
    margin: 0;
    padding: 0;
}
```

A simple reset for unsorted lists.

## Dependency Injection

Dependencies are services or objects that a class needs to perform its function. Dependency Injection (DI) is a coding pattern in which a class asks for dependencies from external sources. DI make your app flexible, efficient and robust as well as testable and maintainable. Let's explain it in practice by creating a own service.

## Services

For your movie app you want to get data from an extern source. [themoviedb.org][104] offers an public api, where you can fetch a json with movie results. Fetch these with your own service. BTW: Services are a great way to share information between components that don't know each other.

## 🔥Practice

[Create a movie service.][02]

Tasks

- [ ] Create in new file `movie.service.ts`
- [ ] Setup the `HttpClient`
- [ ] Subscribe to the service

Notes

- Create in new file `movie.service.ts` in folder `app`
- Use [https://api.themoviedb.org/3/movie/top_rated][104] as api url

Hints

Add the file `movie.service.ts` with the following basic content.

```typescript
// movie.service.ts
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

If you use this command without the flag `--skipTests=true` it will generate additionally the file `movie.service.spec.ts` for testing purpose. Testing is no topic of this workshop. So you can delete or simply ignore this file if generated.

Through DI you supply data to the `AppComponent` from the injectable `MovieService` class. The `@Injectable()` is an essential ingredient in every service definition. It marks it as a service that can be injected. With `providedIn: 'root'` you declare that this service should be created by the root application injector.

### HttpClient

You can use the `HttpClient` to get data from a specific url. But before you can do this you need to import the `HttpClientModule` in file `app.module.ts`. 

```typescript
// app.module.ts
import { HttpClientModule } from '@angular/common/http';

...

@NgModule({
  ...
  imports: [
    ...,
    HttpClientModule
  ],
})
```

Now inject the `HttpClient` in your `movie.service.ts`.

```typescript
// movie.service.ts
import { HttpClient } from '@angular/common/http';
```

Additionally make it available in your class.

```typescript
// movie.service.ts
export class MovieService {

  constructor(
    private http: HttpClient
  ) {}

}
```

Now you can provide a subscription of data in a function for later use in your component.

```typescript
// movie.service.ts
getMovies() {
  return this.http.get('https://api.themoviedb.org/3/movie/top_rated?api_key=d7fc424ee402bd0666f5f420c5201966&page=1&region=CH');
}
```

For a better readability you should outsource the api url in a `const`.

> Excursion: Angular offers environments for development and production. It is possible to have different api urls for the different modes (prod or dev). Therefore you should define the urls in the files provided for. You find them in folder `environments` in you `src` directory. After the property `production` you can define a new property `apiUrl` with the url as value. Then you `import { environment } from '../environments/environment'` in your service and define `const apiUrl = environment.apiUrl` to work with. 

### Subscribe

It's time to `subscribe` to the service to get the data. To do so inject your the movie service in your `app.component.ts`.

```typescript
// app.component.ts
import { MovieService } from './movie.service';
```

Inside the constructor you have access to the service. Time to code the function to subscribe to.

```typescript
// app.component.ts
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

## Templating

We see the data in console. Let's bring it to view. Like we've heard it before we bring data from the controller to the template through interpolation. That means that everthing in double curly braces `{{ ... }}` will be rendered as text. With this text we can do something like display the movie title or add the source url for an image. 

```html
<h2>{{ title }}</h2>
```

The text between the braces is a template expression that Angular first evaluates and then converts to a string. 

```html
<img src="{{path + image}}" ... />
```

With this in mind let's bring up the data into the template.

## 🔥Practice

[Display title and image of each movie.][02]

Tasks

- [ ] Write the data results in an array, e.g. `movies: []`
- [ ] Build the correct image url

Notes

- For building the image src take [https://image.tmdb.org/t/p/original/](https://image.tmdb.org/t/p/original/)

Hint

- In `subsribe` declare `data: any`
- In `subsribe` store it like `this.movies = data.results;`
- You may replace the value of `imageSrc` with the url (see above)
- Build the image src `src="{{imageSrc + movie.poster_path}}"`

## Event binding

With event binding we can listen to events like clicks, touches, mouse movements and keystrokes. Following event binding listens to the `(click)` event of a button and call the `onSave()` method of the component.

```html
<button (click)="onSave()">Click</button>
```

`(click)` = target event name
`onSave()` = template statement

## 🔥Practice

[Create a click event to show the movie title in an alert.][04]

Tasks

- [ ] Code a button in the template with a `(click)` event
- [ ] Transmit the title in the template statement
- [ ] Create an `onClick()` method in your component to catch the title
- [ ] `alert()` the movie title

Hints

For a better reading you can adjust the margin of the headline in `app.component.css`.

```css
/* app.component.css */
h2 {
    margin-top: 120px;
}
```

## $event and event handling

In an event binding, Angular sets up an event handler for the target event. The target event determines the shape of the $event object. For example we use the following `<input>` element (between image and button).

```html
<!-- app.component.html -->
<p>
    <input 
      [value]="movie.title"
      (input)="movie.title=$event.target.value" 
    >
</p>
```

With this example we bind the input `value` with the `movie.title` and listen to changes of the `input` event. From there the property `movie.title` follows the path of `$event.target.value`.

## Stopping propagation

An event on an element in the template will be propagated to it's parent elements unless we will stop it.

```html
<html>
  <body>
    <section>
      <...>
        <button (click)="..." ... >
```

We can stop the propagation by calling the `stopPropagation()` method of an event. Consider following example in your template.

```html
<!-- app.component.html -->
<button (click)="clickIt()">
  <span (click)="clickIt($event)">
    Foo
  </span>
</button>
<button (click)="clickIt()">
  <span (click)="clickIt()">
    Bar
  </span>
</button>
```

Both buttons `Foo` and `Bar` are nested with a `<span>` element, which has the same click event like the parent. So if you click the span you click the button and trigger two click events with one mouse click. To stop this the span of the first button gets the `$event` within the `clickIt()` method.

```typescript
// app.component.ts
clickIt(event?: MouseEvent) {
  const message = event ? 'Propagation stopped!' : 'With propagation :-|';
  alert('Click!' + message);
  if (event) { event.stopPropagation(); }
}
```

Well, our `clickIt()` method takes an `event` parameter (as `MouseEvent`). If this is true, we display a `message` `Click! Propagation stopped!` and call the `stopPropagation()` method. Usually you do this at the end of your event handler.

## 🔥Practice 

[Add an `input` and `click` event.][05]

Tasks 

- [ ] Add the `<input>` example from above to you template
- [ ] Add a `<button>` with a `clickIt()` method
- [ ] Nest the `clickIt()` method inside the button with an `<span>` element

Hints

- Take the examples from above

## @Input

By building a complex app it is necassary from time to time to pass informations between components. In Angular we can pass data from parent to child with input binding. We will use the @Input decorator for this.

## 🔥Practice

[Build a movie detail component and display the movie overview.][04]

Tasks 

- [ ] Generate a interface `movie.ts` and declare `title`, `poster_path` and `overview` as `string`
- [ ] Generate a movie detail component:
  * `movie-detail.component.html`
  * `movie-detail.component.css`
  * `movie-detail.component.ts`
- [ ] Import and declare it in `app.modules.ts`
- [ ] Input the movie data in `.ts`
- [ ] Code the overview template in `.html`
- [ ] Bring the detail into the main template
- [ ] Style the template in `.css`

Notes

You can generate a new interface on cli. Go to the `app` directory of your project and do the following command.

```console
ng generate interface movie
```

This will create a file `movie.ts`, which you can create by hand with the following basic content, if no cli is available.

```typescript
// movie.ts
export interface Movie {
  // title: string;
}
```

You can generate a new component on cli, too.

```console
ng g component movie-detail
```
(`g` is short for `generate`) Or by hand you should create an new folder `movie-detail` in `app` directory and in there three files: `.ts`, `.html` and `.css` with the name `movie-detail.component` as prefix. To make your app familiar with the new component you should import and declare it in `app.modules.ts`. (Now you got an idea of how good cli is.)

```typescript
// app.modules.ts
...
import { MovieDetailComponent } from './movie-detail/movie-detail.component'; // << add this line

@NgModule({
  declarations: [
    AppComponent,
    MovieDetailComponent // << add this line
  ],
...
```

If you have used the cli for generating the component it comes with following basic setup.

```typescript
// movie-detail.component.ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-movie-detail',
  templateUrl: './movie-detail.component.html',
  styleUrls: ['./movie-detail.component.css']
})
export class MovieDetailComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```

In this file you should import the movie interface and initialize it.

```typescript
// movie-detail.component.ts
...
import { Movie } from '../movie'; // << add this line
...
export class MovieDetailComponent {
  @Input() movie: Movie; // << add this line
}
```

This is how your template could look like.

```html
<!-- movie-detail.component.html -->
<div class="detail">
  <p>Overview: {{ movie.overview }}</p>
</div>
```

Then you are able to display the movie overview in your main template.

```html
<!-- app.component.html -->
<li *ngFor="let movie of movies">
  ...
  <app-movie-detail [movie]="movie"></app-movie-detail>
</li>
```

For a better reading on desktops fit the width of a list item (parent item) in css.

```css
/* app.component.css  */
@media only screen and (min-width: 768px) {
    li {
        width: 50vw;
        margin-left: auto;
        margin-right: auto;
    }
}
```

Maybe at this point you think Angular is a little bit to much for just displaying the overview. In this case you are right. But the benefit comes on a larger scale and when it comes to testing (no topic of this workshop).

## @Output

If you input some data from component to component you may want to output some data, too. As the `@Input` practice before Angular offers you a decorator for this: `@Output`.

## EventEmitter

Continue Angular provides an `EventEmitter` class which is used when publishing values from a component through the `@Output()` decorator. EventEmitter adding an `emit()` method so it can send values. A childs `EventEmitter` property is an `@Output` property. 

## 🔥Practice

[Emit an event of your parent component to display the selected movie from the detail component.][07]

Tasks

- [ ] Add `active: boolean` to the Movie interface `movie.ts` for toggling
- [ ] Add a `<button>` to `movie-detail.component.html` to `Activate` or `Deactivate` the movie and call an `(click)` event with a `choose()` method
- [ ] Add the method `choose()` in `movie-detail.component.ts` to toggle the selected movie and to ...
- [ ] Emit `this.movie` to the parent with `@Output` and `EventEmitter`; take `chooseRequest` as given event name
- [ ] Prepare the parent template with `chooseRequest` event to call a method `chooseMovie()` 
- [ ] Write a `chooseMovie()` method with `movie` parameter (interface `Movie`) to  simple `alert()` an `alertMessage` and the `movie.title`
- [ ] Define the `background-color` for the `active` `li` element with CSS

Hints

- With `active: boolean` you can toggle the button text in your child component from `Deactivate` to `Activate` and vice versa. Furthermore it will be useful to take this boolean for adding css classes in the list item of your parent component.

```html
<!-- app.component.html -->
<li ...
[className]="movie.active ? 'active' : 'inactive'"
>
```

- In the `[className]` you can write an expression, e.g. to toggle the classes `active` and `inactive`

```html
<!-- movie-detail.component.html -->
<p>
  <button (click)="choose()">
    <span [innerHTML]="movie.active ? 'Deactivate' : 'Activate'"></span>
  </button>
</p>
```

- The `<button>` in `movie-detail.component.html` should come with a `(click)` event to call the new method `choose()` for example. In a `<span>` and with the `[innerHTML]` property you manipulate the button text by the `movie.active` boolean. It should be `Deactive` by default and `Activate` by clicking.

```typescript
// movie-detail.component.ts
import { ... EventEmitter, Output } from '@angular/core';
```

- For the next steps we keep in mind that we want to pass some data from the child component to the parent. In our case it is the selected `movie` object. Furthermore we want to trigger a parent event `(chooseRequest)` with it. This event doesn't exist at this very moment but it will be come with an own method. Well, step by step. Next additionally import the `EventEmitter` and `Output` from the `core`. 

```typescript
// movie-detail.component.ts
@Output() chooseRequest = new EventEmitter<Movie>();
```

- Your detail component can now expose an EventEmitter property. The parent binds to that event property and will react with an own method . `chooseRequest` will be the parent event.

```typescript
// movie-detail.component.ts
choose() {
  this.movie.active = !this.movie.active;
  this.chooseRequest.emit(this.movie);
}
```

- Next you toggle `this.movie.active` property to `true`. At least in your detail component you `emit` `this.movie` to `chooseRequest`.

```html
<!-- app.component.html -->
<app-movie-detail 
  [movie]="movie" 
  (chooseRequest)="chooseMovie($event)"
>
</app-movie-detail>
```

- Time to prepare the parent to listen to the child by adding the `(chooseRequest)` event to call the `chooseMovie()` method, which will be coded next.

```typescript
// app.component.ts
chooseMovie(movie?: Movie) {
  const alertMessage = movie.active ? 'Activated' : 'Deactivated';
  alert(alertMessage + ` ${movie.title}.`);
}
```

- The `chooseMovie()` method have `movie?: Movie` as parameter. To call a simple `alert()` you toggle an `alertMessage` and display the `movie.title`, which is be given from the child through parameter.

```css
/* app.component.css */
li {
    transition: background-color 0.3s ease;
    padding: 40px;
    margin-bottom: 40px;
}

...

.active {
    background-color: lightblue;
}
```

- The toggling of the `background-color` looks better in `transition`. (You may delete an existing `h2` definition for a better result.)

## Final app 🎉

[Final movie app.][08].

... to be continued ...

[//]: # (app links)
[00]: https://stackblitz.com/github/Bloggerschmidt/abw-start/ "StackBlitz Angular Beginners Workshop (ABW) Starter App"
[01]: https://stackblitz.com/github/Bloggerschmidt/abw-s01 "ABW Movie App Version 1"
[02]: https://stackblitz.com/github/Bloggerschmidt/abw-s02 "ABW Movie App Version 2"
[03]: https://stackblitz.com/github/Bloggerschmidt/abw-s03 "ABW Movie App Version 3"
[04]: https://stackblitz.com/github/Bloggerschmidt/abw-s04 "ABW Movie App Version 4"
[05]: https://stackblitz.com/github/Bloggerschmidt/abw-s05 "ABW Movie App Version 5"
[06]: https://stackblitz.com/github/Bloggerschmidt/abw-s06 "ABW Movie App Version 6"
[07]: https://stackblitz.com/github/Bloggerschmidt/abw-s07 "ABW Movie App Version 7"
[08]: https://stackblitz.com/github/Bloggerschmidt/abw-s08 "ABW Movie App Version 8"

[//]: # (reference links)
[101]: https://angular.io/guide/architecture "Angular - Architecture overview"
[102]: https://medium.com/google-developers/exploring-es7-decorators-76ecb65fb841 "Exploring EcmaScript Decorators"
[103]: https://angular.io/guide/observables "Angular Official Documentation - Observables"
[104]: https://api.themoviedb.org/3/movie/top_rated?api_key=d7fc424ee402bd0666f5f420c5201966&page=1&region=CH "api.themoviedb.org"

[//]: # (image links)
[1001]: images/stackblitz.com-abw-start.png "Screenshot StackBlitz Angular beginners workshop starter app"
