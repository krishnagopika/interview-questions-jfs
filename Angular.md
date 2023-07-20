1. Demonstrate a basic understanding of Angular or What is Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
  <summary> <b>Show Answer</b></summary>
  
<blockquote>
  
- Angular is a typescript-based web application framework used to create & build web apps
- It allows us to create Single Page Applications (SPA)
- Gmail, Youtube, and PayPal apps are developed using Angular

</blockquote>
</details>

--- 

2. What is meant by SPA? _or_ Give some examples of single-page applications.

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
  
<blockquote>

- It is a single web page, website, or web application that works within a web browser and loads just a single document.
- It does not need page reloading during its usage, and most of its content remains the same while only some of it needs updating.
- **Gmail**, **Facebook**, **Trello**, **Google Maps**, etc., all are Single Page Applications that offer an outstanding user experience in the browser with no page reloading.

</blockquote>
</details>

--- 

3. Angular workflow _or_ How does Angular work or bootstrapping your angular app? _or_ How do you load an Angular application in the webserver? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
  
<blockquote>
  
- Flow: `angular.json`-> `main.ts` -> `AppModule` -> `AppModule` -> `index.html`.
- Every Angular app consists of a file named `angular.json` . This file will contain all the configurations of the app. While building the app, the builder looks at this file to find the entry point of the application.

![image](https://user-images.githubusercontent.com/103101208/185569359-55632ef6-971e-47d9-a7bf-96a1de37026e.png)
  
- Inside the build section, the main property of the options object defines the entry point of the application which in this case is `main.ts`.
- `main.ts` is the entry point of the angular application. 
- The `main.ts` file creates a browser environment for the application to run, and, along with this, it also calls a function called bootstrap module, which bootstraps the application. These two steps are performed in the following order inside the `main.ts` file:
	
![image](https://user-images.githubusercontent.com/103101208/185569651-35a2ba9f-73fc-43c6-8548-0a24daac640b.png)
- In the above line of code, `AppModule` is getting bootstrapped.
- The `AppModule` is declared in the `app.module.ts` file. This module contains declarations of all the components.
- Below is an example of the `app.module.ts` file:
	
![image](https://user-images.githubusercontent.com/103101208/185569778-9ff0d34a-b0e2-4701-a1db-21919ebd3ad7.png)
	
- As one can see in the above file, `AppComponent` is getting bootstrapped.
- This component is defined in the `app.component.ts` file. This file interacts with the webpage and serves data to it.
- Below is an example of the `app.component.ts` file:
  
 ![image](https://user-images.githubusercontent.com/103101208/185569886-8ca076a7-6633-4d61-beb5-0d673014b347.png)

- After this, Angular calls the `index.html` file. This file consequently calls the root component that is `app-root`. 
- This is how the `index.html` file looks:
	
![image](https://user-images.githubusercontent.com/103101208/185569990-6c67e5b0-d9a6-4340-b2f0-dcd9a9f738c5.png)
	
- The HTML template of the root component is displayed inside the `<app-root>` tags.
- This is how every angular application works. Or This is how angular applications get bootstrapped

  </blockquote>
</details>
	
--- 
  
4. How SPA is different from traditional webapplicationsn?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
- In traditional web technology, the client requests for a web page (HTML/JSP) and the server sends the resource (or HTML page), and the client again requests for another page and the server responds with another resource. 
- The problem here is a lot of time is consumed in the requesting/responding or due to a lot of reloading. 
- Whereas, in the SPA technology, we maintain only one page (`index.html`) even though the URL keeps on changing. 

  </blockquote>

</details>
  
 ---
  
5. Have you used Angular in your project? Can you list some of the features of Angular?
  
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Yes, used Angular.
	
- Angular written using TypeScript
- Angular uses Databinding and Routing
- Angular uses Jasmine testing framework

</blockquote>
</details>
  
 ---
  
6. In SPA, after the initial page load, does the server send any more HTML to you?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

On a SPA, after the initial page load, no more HTML gets sent over the network. Instead, only data gets requested from the server (or sent to the server).
	
</blockquote>
</details>
  
 ---
  
7. Does refreshing a whole page needed in SPA?
	
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

In a SPA, a page refresh never occurs; instead, all necessary HTML, JavaScript, and CSS code are either retrieved by the browser with a single page load, or the appropriate resources are dynamically loaded and added to the page as necessary, usually in response to user actions.
	
</blockquote>
</details>
  
---
  
8. What are some advantages of Angular?
  
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
  
  <blockquote>
    
- Effective cross-platform development
- Two-way data binding in Angular will help users to exchange data from the component to the view and the room view to the component.  It will help users to establish communication bi-directionally. 
- The Angular command-line interface (CLI) makes the developer’s job easier because it offers a set of helpful tools for coding. 
- Angular offers powerful DI (dependency injection) instruments and services to resolve various productivity issues and speed up the development process.
- Modularity of angular application makes our code readable and testable

</blockquote> 

</details>
	
--- 
	
9. What do you choose between Traditional Web Apps and Single Page Apps _or_ What do you choose between Multiple Page Apps and Single Page Apps

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
Choose based on the explanation given
</blockquote> 
	
<details>
<summary><b>Explanation</b></summary>
<blockquote>
	
Use traditional web applications or MPA when:
- Your application's client-side requirements are simple or even read-only.
- Your application needs to function in browsers without JavaScript support.

Use a SPA when:

- Your application must expose a rich user interface with many features.
- Your team is familiar with JavaScript, or TypeScript.
- Your application must already expose an API for other (internal or public) clients.

Both SPA and MPA are not flawless as they have their pros and cons. SPA is the best choice if you care about **speed and code reusability** that can be applied to develop a **mobile app**. However, it has deficiencies in SEO optimization. MPAs win in case you strive to be **ranked higher in Google**, and it is more scalable but much slower than single-page applications.

Choosing the best option, you should always have your business goals and requirements in mind.

</blockquote> 
</details>
</details>

---

10. How is SPA different from MPA?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
A SPA is an app that works inside a browser and does not require page reloading during use.

On the other hand, an MPA multiple-page application) is considered a more traditional approach to app development. The multi-page design pattern requires a page reload every time the content changes. It’s a preferred option for large companies with extensive product portfolios, such as e-commerce businesses.	
	
</blockquote> 
</details>

---

11. Difference between Angular JS and Angular 4 +

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

| **Angular JS**                                                                                     | **Angular 4**                                                                                                                    |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Uses MVC architecture to build the applications.                                                   | Uses component-based UI to build the applications.                                                                               |
| AngularJS is written in JavaScript.                                                                | Angular is compatible with the most recent versions of TypeScript that have powerful type-checking and object-oriented features. |
| To bind an image/property or an event with AngularJS, you have to remember the right ng directive. | Angular focuses on “()” for event binding and “\[ \]” for property binding.                                                      |
| AngularJS doesn't support mobiles.                                                                 | Angular support mobiles.                                                                                                         |

</blockquote>

</details>
	
--- 

12. Difference between Angular 2 and Angular 4
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

| **Angular 2**                                                                      | **Angular 4**                                                                                       |
| ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Angular v2.0 uses Typescript, a superset of JavaScript, for writing the application. | Angular v4.0 serves to be compatible with the new version of TypeScript 2.1 as well as TypeScript 2.2. |
| Code is not Reduced much                                                           | Reduce the size of the generated bundled code up to 60%                                             |

</blockquote>

</details>
	
--- 

13. What are some common Angular CLI commands?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
- `ng  new MyApp` – used to create an angular application named ‘MyApp’
- `ng new MyApp  --routing`  - used to create an angular application named ‘MyApp’ with the routing module
- `ng g c first` – used to create a component named ‘first’
- `ng g p changePipe` – used to create pipe named `changePipe’
- `ng g s user` -  used to create a service named ‘user’
- `ng serve` – used to build, run and launch applications on HTTP port 4200
- `ng serve -o` -  used to build, run and launch applications on HTTP port 4200, -o option automatically opens the browser to [ http://localhost:4200]( http://localhost:4200)
	
</blockquote>
</details>
	
--- 
	
14. What does `ng` means?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
- `ng` stands for A**ng**ular
	
</blockquote>
</details>
	
--- 
	
15. List drawbacks and benefits of MPA _or_ List the advantages and disadvantages of MPA

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
Benefits:
- Performs well on the search engine.
- Provides a visual map of the web app to the user.

Drawbacks:
- Comparatively complex development
- Coupled backend and frontend
	
</blockquote>
</details>
	
--- 
	
16. List drawbacks and benefits of SPA _or_ List the advantages and disadvantages of SPA

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
Benefits:
- Single Page Apps are smooth and fast.
- They are easy to develop and deploy.
- SPAs are easier to debug.
- Can be transited to mobile apps by reusing the same backend code.

Drawbacks:
	
- SPAs perform poorly on the search engine. But now, with isomorphic rendering/server-side rendering even SPAs can be optimized for search engines too.
- Single-page applications provide single-sharing links.
- They are less secure compared to traditional multi-page apps because of their cross-site scripting.
	
</blockquote>
</details>
	
--- 

17. What is the latest version of Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
- Angular 14 (as of August 2022)
	
</blockquote>
	
<details>
<summary> <b>Reference</b></summary>
<blockquote>

[Angular versioning and releases](https://angular.io/guide/releases)
	
</blockquote>
</details> </details>
	
--- 
	
18. Does Angular support mobiles?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

 Yes, we can create a mobile application using Angular Framework. 
	
</blockquote>
</details>
	
--- 
	
19. Why do we need Webpack?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- In our web application, we use many javascript files that are added to the HTML pages via `<script>` tags.  For each user request, the browser loads these bunch of script files inside the HTML page. This is inefficient as it reduces the page speed since the browser requests each script file separately.
- This can be solved by **bundling** several files together into one file to be downloaded by the browser in one single request.
- **Module bundlers** are used to bundle a group of JavaScript modules with their dependencies and merge them into a single file in the correct order, which can be executed by the browser.
- **Webpack** is a powerful static module bundler for JavaScript applications that packages all modules in our application into a bundle and serves it to the browser. Webpack builds a dependency graph when it processes the application. 
		
</blockquote>
</details>
	
--- 
	
20. Webpack builds a dependency graph. What does that mean? _or_ What is a dependency graph? How is it related to Webpack?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- Any time one file depends on another, webpack treats this as a dependency. This allows webpack to take images or web fonts, and also provide them as dependencies for your application.

- When webpack processes your application, it starts from a list of modules defined on the command line or in its configuration file. Starting from these entry points, webpack recursively builds a dependency graph that includes every module your application needs, then bundles all of those modules into a small number of bundles - often, only one - to be loaded by the browser.
		
</blockquote>
</details>
	
--- 

21. How do you install Angular CLI?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

Before installing Angular CLI, make sure the development environment includes Node.js and an npm package manager. Then, run the command `npm install -g @angular/clip on the terminal to install the Angular CLI using npm.
		
</blockquote>
</details>
	
--- 
	
22. How do you create any angular application?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

Run the CLI command `ng new my-app to create a new angular app with the `my-app` name.

</blockquote>
</details>
	
--- 

23. Which port angular application will be launched?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

4200

</blockquote>
</details>
	
--- 

24. How `ng serve -o` different form `ng serve` command?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

The `ng serve` command launches the server on HTTP port 4200, which watches our files and rebuilds the app as we make changes to those files. The --open (or just -o) option automatically opens the browser to [http://localhost:4200](http://localhost:4200).
	
</blockquote>
</details>
	
--- 

25. How do you find the version of angular installed in our system?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

To check the version of angular installed by running the `ng --version` or `ng v` command
	
</blockquote>
</details>
	
--- 

26. How do you update angular to the latest version?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
Run the `npm install -g @angular/cli@latest` command to update angular to the latest version.

</blockquote>
</details>
	
--- 

27. What is the difference between `npm start` and `ng serve`?
	
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

`npm start` will run whatever you have defined for the start command of the scripts object in your `package.json` file.

So if it looks like this:
```ts
"scripts": {
  "start": "ng serve"
}
```

Then `npm start` will run `ng serve.

The `ng serve` commis and used when developing your application locally. It starts up a local development server, which will serve your application while you are developing it.

</blockquote>
</details>
	
--- 
	
28. How to deploy the angular app to production?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- `ng build` command is used to build your application and deploy it. 
- `ng serve --prod` command to run when building your application for a production environment

</blockquote>
</details>
	
--- 
	
29. What kind of files we can find in the _e2e_ folder and node_modules folder?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

The _e2e_ folder at the top level contains source files for a set of end-to-end tests and test-specific configuration files. The _node_modules_ folder provides npm packages to the entire workspace.
	
</blockquote>
</details>
	
--- 
	
30. What are files we can find under the _src_ folder?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
The _src_ folder contains the source files which give information about application logic, data, and assets. It has

</blockquote>
</details>
	
--- 
31. What is the difference between the `angular.json` and `package.json` files?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

`angular.json` - holds CLI configuration defaults for all projects in the workspace. It includes configuration options for the build, serves, and test tools.
	
`package.json` - used to configure npm package dependencies that are available to all projects in the workspace.

</blockquote>
</details>
	
--- 
32. What is the difference between `package.json` and `package-lock.json` files?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

`package.json` - used to configure npm package dependencies that are available to all projects in the workspace.

`package-lock.json` - this provides version information for all packages installed into _node_modules_ by the npm client.
	
</blockquote>
</details>
	
--- 
	
33. Why do need to compile the Angular? 
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>	
	
Angular is written using TypeScript. But, the browser only understands JavaScript. We need to compile the Angular, so angular applications require a compilation process before they can run in a browser.
	
</blockquote>
</details>
	
--- 

34. Have you heard of the AOT compiler? If so, can you explain it?
		
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>	
	
The Angular ahead-of-time (AOT) compiler converts your Angular HTML and TypeScript code into efficient JavaScript code during the build phase before the browser downloads and runs that code. Compiling your application during the build process provides a faster rendering in the browser.
	
</blockquote>
</details>
	
--- 
	
35. Do you recommend an AOT compiler? If yes, Justify.
		
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>	

Yes, I recommend the AOT compiler. Here are my reasons:

- **Faster rendering**: With AOT, the browser downloads a pre-compiled version of the application. The browser loads executable code so it can render the application immediately, without waiting to compile the application first.
- **Detect template errors earlier**: The AOT compiler detects and reports template binding errors during the build step before users can see them.
- **Better Security**: AOT compiles HTML templates and components into JavaScript files long before they are served to the client. With no templates to read and no risky client-side HTML or JavaScript evaluation, there are fewer opportunities for injection attacks.
		
</blockquote>
</details>
	
--- 

36. Can you tell me about the JIT compiler?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Just in time (JIT) compiler provides compilation during the execution of the program at a run time before execution. In simple words, code gets compiled when it’s needed, not at the build time.

</blockquote>
</details>
  
---
 	

37. How JIT compiler differs from the AOT compiler?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

| JIT                                                                                            | AOT                                                                                                               |
|------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| JIT downloads the compiler and compiles code exactly before Displaying it in the browser.         | AOT has already complied with the code while building your application, so it doesn’t have to compile at runtime. |
| Loading in JIT is slower than the AOT because it needs to compile your application at runtime. | Loading in AOT is much quicker than the JIT because it already has compiled your code at build time.              |
| JIT is more suitable for development mode.                                                     | AOT is much more suitable in the case of Production mode.                                                              |
| Bundle size is higher compared to AOT.                                                          | Bundle size optimized in AOT, in results AOT bundle size is half the size of JIT bundles.                         |
| You can run your app in JIT with this command: `ng build` OR `ng serve`                            | To run your app in AOT you have to provide –aot at the end like: `ng build --at OR `ng serve --not                 |
| You can catch template binding errors at display time.                                          | You can catch the template error at building your application.                                                    |

</blockquote>
</details>
  
---
	
38. When to use JIT Compiler?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- If you have a big project or a situation where some of your components don’t come in use most of the time then you should use the Just in time compiler.
- Just in Time compiler is best when your application is in local development

</blockquote>
</details>
  
---
	
39. Let us take a most commonly used application, youtube or E-mail. How do you see Angular in this application? 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
  <summary> <b>Show Answer</b></summary>
  
<blockquote>
  
- Angular is a typescript-based web application framework used to create & build web apps
- It allows us to create Single Page Applications (SPA)
- Angular written using TypeScript
- Angular uses Databinding and Routing
- Angular uses Jasmine testing framework

**NOTE** - The candidate must come up with the angular points that they see in the application. Depends on the candidate. This makes the interviewer understand how far the candidate can relate a real-time application to the topic

</blockquote>
</details>

--- 
	
40. Is Angular Javascript-based or Typescript based?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
  <summary> <b>Show Answer</b></summary>
  
<blockquote>

- AngularJS is written using JavaScript
- Angular 2+  written using TypeScript

</blockquote>
</details>

---

1. What is a component?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Components are the basic building blocks in the Angular application. Components contain the data & UI logic that defines the view and behavior of the web application.

![image](https://user-images.githubusercontent.com/70228962/186086415-c49cc203-e383-43c0-bc5b-15e2f101f159.png)

Consider, we are building a page for an application. The features on the page include the header, footer and navigation, and content area. Instead of building a single page with all these features, we can choose to split the page into components, which helps us to manage our application. In the above scenario, we can say that the header, footer, content area, navigate, on, and so on are separate components of the page; but when the user views it on the website through any device, it will show as a single page.
	
</blockquote>
</details>
  
---

2. In which file, I can find the `@Component` decorator?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
 `app.component.ts` 
  
</blockquote>
</details>
  
---

3. How do you create a component?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
 Run the `ng generate component <component_name>` or `ng g c <component-name>` command in the terminal to create a component

</blockquote>
</details>
  
---
  
 4. What are the files created or updated when we create a component? _or_  How would you create an HTML file along with a component?
 
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
  
<details>
<summary><b>Show Answer</b></summary>
<blockquote>
   
When we run `ng g c server` in the terminal, CLI creates a component and registers this component in the AppModule. Now, you're able to see a `server` folder inside `src/app`. This `server` folder contains 4 files - `server.component.html`, `server.component.spec.ts`, `server.component.ts` and `server.component.css`. 

</blockquote>
</details>
  
---
  
5. Angular Components Lifecycle or Lifecycle Hooks or LifeCycle Methods
  
<details>
<summary> <b>Show Answer</b></summary>
  
<blockquote>
  
Angular creates a component; renders it; creates and renders its children; checks it when its data-bound properties change; and destroys it before removing it from the DOM. These events are called "Lifecycle Hooks".
	
Lifecycle Hooks:	.
- `non changes()` - Called whenever the input properties of the component change. It returns a simple changes object which holds any current and previous property values.
- `ngOnInit()` - Called once to initialize the component and set the input properties. It initializes the component after Angular first displays the data-bound properties.
- `ngDoCheck()` - Called during all change-detection runs that Angular can't detect on its own. Also called immediately after the `ngOnChanges()` method.
- `ngAfterContentInit()` - Invoked once after Angular performs any content projection into the component’s view.
- `ngAfterContentChecked()` - Invoked after each time Angular checks for content projected into the component. It's called after `ngAfterContentInit()` and every subsequent `ngDoCheck()`
- `ngAfterViewInit()` - Invoked after Angular initializes the component's views and its child views.
- `ngAfterViewChecked()` - Invoked after each time Angular checks for the content projected into the component. It called after `ngAfterViewInit()` and every subsequent `ngAfterContentChecked()`
- `ngOnDestroy()` - Invoked before Angular destroys the directive or component.


NOTE - `constructor()` - The constructor of the component class gets executed first, before the execution of any other lifecycle hook events. If we need to inject any dependencies into the component, then the constructor is the best place to do so
	
</blockquote>  
</details>
	
---  

6. What is the use of the `@Component` decorator?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- Components in Angular are defined using a `@Component` decorator. It includes a selector, template, style, and other properties, and it specifies the metadata required to process the component.

</blockquote>
</details>
  
---

7. How many components can angular have?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Angular applications can have multiple components. Each component handles a small part of the UI. These components work together to produce the complete user interface of the application.

</blockquote>
</details>
  
---

8. What is the root component in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

An Angular application has one root component - `AppComponent`

</blockquote>
</details>
  
---
	
9. How do you find which is a root component?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

By default, the root component in angular is `AppComponent` which is specified in the `bootstrap` array under the `@NgModule` defined in the `app.module.ts` file.

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
	
</blockquote>
</details>
	
---

10. I have to create the component `user` as a parent. Then, I want to 2 child components for the `user` component. Let's say 2 child components are `user-login` and `user-register`. What are the steps I needed to do?
	
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

**Steps:**
1. Run `ng g c user` in the terminal, CLI creates a component and registers this component in the AppModule.  Now, you're able to see a `user` folder inside `src/app`.
2. Move to the `src/app/user` folder.
3. Run `ng g c user-login` in the terminal, CLI creates the `user-login` component
4. Run `ng g c user register in the terminal, CLI creates `the user register component

![image](https://user-images.githubusercontent.com/70228962/186089554-ec5c403b-dd95-4f13-83ce-2bd90e4b67c2.png)

</blockquote>
</details>
  
---
	
11. Below is the code in `user.component.ts`. If I want to insert a user component to the `index.html` file.
```ts
import { Component } from '@angular/core';
@Component ({
  selector: 'user'
  templateUrl: './user.component.html' ,
  styleUrls: ['./user.component.css']
export class UserComponent {
} 
```
 
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Using the `<user>` tag in the `index.html`

</blockquote>
</details>
  
---
	
12. Detail about `@Component` Decorator.
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)	

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

In the `app.component.ts` file, we export the `AppComponent` class, and we decorate it with the `@Component` decorator, imported from the `@angular/core package`, which takes a few metadata, such as: `selector`, `templateUrl` and `styleUrls`.

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'angularDemoProject';
}
```
- `selector` – just the name given for the component. In the `index.html` file, the `<app-root>` tag corresponds to the component’s selector. By doing so, Angular will inject the corresponding template of the component. 
```html
<body>
  <app-root></app-root>
</body>
```
- `templateUrl` - points to an HTML file that defines what you see on your application. 
- `styleUrls` - points to a set of CSS files that define styles or designs for the  application

</blockquote>
</details>
	
---   

13. What is a template in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

A template is just like regular HTML that renders a view, or user interface, in the browser.

When you generate an Angular application with the Angular CLI, the `app.component.html` file is the default template containing placeholder HTML.

</blockquote>
</details>
  
---
 
 14. What is the difference between `templateUrl` and `template` in the `@Component` decorator?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- `templateUrl` - You can define the template in a separate HTML file and link to it in the component metadata using the `@Component` decorator's `templateUrl` property.
	
- `template` - You can define it inline using the template property 
</blockquote>
</details>
  
---
 	
	
15. What is the difference between `styleUrls` and `styles` in the `@Component` decorator?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
- You can use the `styles` property to keep the CSS code in line to style your component's HTML template.
```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styles:[`
        .green { color:#003300 !important; }
        .bold { font-weight:bold; }
        `]
})
```
- You can use the `styleUrls` property Keep the CSS code separately in your file to style your component's HTML template.
	
```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
```
- **NOTE:** Both the `styles` and `styleUrls` properties are arrays.

</blockquote>
</details>
  
---
 
16. Which lifecycle hook will be executed first?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`OnChanges()`

</blockquote>
</details>
  
---
 
17. Where I can inject any dependencies into the component?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`constructor()`

</blockquote>
</details>
  
---
 
18. In which order do lifecycle hooks get executed?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Angular calls these hook methods in the following order:

1. **`ngOnChanges`**: When an input/output binding value changes.
2. **`ngOnInit`**: After the first `ngOnChanges`.
3. **`ngDoCheck`**: Developer's custom change detection.
4. **`ngAfterContentInit`**: After component content initialized.
5. **`ngAfterContentChecked`**: After every check of component content.
6. **`ngAfterViewInit`**: After a component's views are initialized.
7. **`ngAfterViewChecked`**: After every check of a component's views.
8. **`ngOnDestroy`**: Just before the component/directive is destroyed.

</blockquote>
</details>
  
---
 
19. Which lifecycle hook is called only one?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`ngOnInit`called only once during the component lifecycle, after the first `ngOnChanges` call. 

</blockquote>
</details>
  
---
 
20. Which angular module has all lifecycle hooks interfaces?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`@angular/core`

</blockquote>
</details>
  
---
	
21. Can we have HTML content attached to the component without having a `.html` file? If so, how?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Yes, by using an inline template.
	
Inline Template  - It is defined by placing the HTML code in backticks _`_ and is linked to the component metadata using the `template` property of `the @Component` decorator.
```ts
@Component({
  selector: 'app-root',
  templateUrl: `<h1> Hello World </h1>`,
  styleUrls: ['./app.component.css']
})
````

</blockquote>
</details>
  
---
	
22. Can we have CSS styles attached to the component without having a `.css` file? If so, how?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Yes, by using inline CSS. 

You can use the `styles` property to keep the CSS code inline to style your component's HTML template.
```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styles:[`
        .green { color:#003300 !important; }
        .bold { font-weight:bold; }
        `]
})
```
	
</blockquote>
</details>
  
---
	
23.  Can we have a multiline template? If so, how?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
Yes, by using backticks _`_
	
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `<h1> Hello World </h1>
  <h2> Hello World  </h2>
  ` ,
  styleUrls: ['./app.component.css']
})
export class AppComponent{
  title = 'angularDemoProject';
}
```
	
</blockquote>
</details>
  
---
	
24. What are our views on Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Views are almost like their own virtual DOM.  Together, the component and its template describe a view.

</blockquote>
</details>
  
---
	
25. How view is different from a template?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

A template is an HTML snippet that tells Angular how to render the component in an angular application.

The template is immediately associated with a component that defines that component’s view.

</blockquote>
</details>
  
---

26. What are ways to define templates?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

There are two ways of defining a template in an angular component.
1. Inline Template
2. External Template
	
Inline Template  - It is defined by placing the HTML code in backticks _`_ and is linked to the component metadata using the `template` property of `the @Component` decorator.
```ts
@Component({
  selector: 'app-root',
  templateUrl: `<h1> Hello World </h1>`,
  styleUrls: ['./app.component.css']
})
````
External Template - It is defined in a separate HTML file and is linked to the component metadata using the `@Component` decorator’s `templateUrl` property 
	
```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
```

</blockquote>
</details>
  
---
 
27. What would you choose between the inline and external template files?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Choose based on the explanation below	

</blockquote>
<details>
<summary><b>Explanation</b></summary>
<blockquote>

Normally we use inline templates for small portion of code and external template files for bigger views. By default, the Angular CLI generates components with a template file. But you can override that with using `ng g c hero -it` command.
	
</blockquote>
</details>
</details>
  
---
 
28. What is executed before any lifecycle hooks? 
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`constructor()`

</blockquote>
</details>

---

29. Complete the missing metadata in `@Component` decorator with following criteria.
    -  This component should be identified by `user`
    -  Template of this component, should say "Hello User!!"
    -  Template should have at least one heading tag
    -  Also, the text inside that heading tag, should be in red color
```ts
import { Component } from '@angular/core';
@Component ({
  // add here
export class UserComponent {
} 
```	
	
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
```ts
import { Component } from '@angular/core';
@Component ({
selector: 'user',
  template: `<h1> Hello User!!</h1>  ` ,
  styles: `[h1 { color: red; }]`
})
export class UserComponent {
} 
```	
	
</blockquote>
</details>
  
---
	
30. What happens if you use the `<script>` tag inside the template?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- Angular recognizes the value as unsafe and automatically sanitizes it, which removes the `<script>` tag but keeps safe content such as the text content of the script tag. 
- This way it eliminates the risk of **script injection attacks**. 
- If you still use it then it will be ignored and a warning appears in the browser console.
	
</blockquote>
</details>
  
---
	
31. What is the difference between `constructor()` and `ngOnInit()`?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
The _constructor_ is a _Typescript_ feature used to instantiate the _Typescript_ class. In most Angular projects the only thing that should ever be done in the constructor is to inject services.

The _ngOnInit_ function is specific to the Angular framework and is called when Angular is done creating the component. It should be called with any custom finalization like loading data for your component to display.
	
</blockquote>
</details>
  
---

32. What is a dynamic component in Angular?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Dynamic components are components’ location in the application that is not defined at build time. That means, that it is not used in any angular template.

Instead, the component is instantiated and placed in the application at runtime.

</blockquote>
</details>
  
---
	
33. What is View Encapsulation in Angular?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

View Encapsulation in Angular defines how the styles defined in the template affect the other parts of the application. 

</blockquote>
</details>
  
---
 
34. List the strategies that angular uses while rendering the view?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

3 strategies - `ViewEncapsulation.Emulated`, `ViewEncapsulation.ShadowDOM` and `ViewEncapsulation.None`
	
</blockquote>
</details>
  
---
	
35. Why do we need View Encapsulation?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>	
	
The CSS Styles have global scope. CSS rules apply to the entire document. You cannot apply rules to the part of the document. Hence, we use class, id & CSS specificity rules to ensure that the styles do not interfere with each other

In the case of Angular apps, the components co-exists with the other components. Hence it becomes very important to ensure that the CSS Styles specified in one component do not override the rules in another component.
	
That's why we need view encapsulation.
	
</blockquote>
</details>
  
---
		
36. How do add view encapsulation to components?
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>	
	
The Encapsulation methods are added using the encapsulation metadata of the @Component decorator as shown below:

```ts
@Component({
  template: `<p>Using Emulator</p>`,
  styles: ['p { color:red}'],
  encapsulation: ViewEncapsulation.Emulated     //This is the default
//encapsulation: ViewEncapsulation.None
//encapsulation: ViewEncapsulation.ShadowDOM
})
```

**NOTE:** `ViewEncapsulation.Emulated` is the default encapsulation method.
	
</blockquote>
</details>
  
---
			
1. Why do we need Node.js for Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- We use Node.js and npm as tools for building Angular or React apps. 
- Angular is a front-end framework used to create a web application and is written in **Typescript**. 
- The **browser only understands JavaScript code**, so we need to compile Typescript (.ts file) to plain JavaScript (.js file). 
- We use Node.js and npm to perform this compilation, then we can deploy them in production.

</blockquote>
</details>
  
---

2. How do you install node and npm?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

- Download Node.js from nodejs.org and install it. 
- The npm CLI gets installed with Node.js by default. 
- To check that you have installed npm, run `npm -v` in a  terminal. 
- **NOTE:** npm can install packages in a node_modules folder in angular working directory.

</blockquote>
</details>
  
---

3. What is the use of Node.js?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
- Node.js is an open-source, cross-platform run-time environment built on Chrome's V8 JavaScript engine.
- Node.js is used to execute JavaScript code outside of a web browser. It provides a library of various JavaScript modules, which simplifies the development of web applications.
- Global companies like Netflix, Facebook, Walmart Linkedin, Uber, etc., use Node.js for building their applications. 
  
</blockquote>

</details>
  
---

4. What is NPM?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
 
- NPM stands for Node Package Manager, responsible for managing all the packages and modules for Node.js.

- Node Package Manager provides two main functionalities:
    - Provides online repositories for node.js packages/modules, which are searchable on search.nodejs.org
    - Provides command-line utility to install Node.js packages and also manages Node.js versions and dependencies  
  
</blockquote>

</details>
  
---

5. What is the difference between Angular and Node.js?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

|                           Angular                           |                                 Node.js                                 |
|:-----------------------------------------------------------:|:-----------------------------------------------------------------------:|
|            It is a frontend development framework           |                     It is a server-side environment                     |
|                 It is written in TypeScript                 |                    It is written in C, C++ languages                    |
| Used for building single-page, client-side web applications | Used for building fast and scalable server-side networking applications |
 
</blockquote>

</details>
  
---

6. How do you check whether Node.js is installed successfully in your system?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

To check that node.js is installed, open the power shell or command prompt (cmd) and type `node –v`. If the node is installed tall properly in your system print something like that v4.4.3.

</blockquote>
</details>
  
---
 
7. What kind of information we can find in the `package.json` file?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

 `package.json` file is used to store the metadata related to the project such as a project description, the version of the project in a particular distribution, and license information, as well as to store the list of dependency packages.

</blockquote>
</details>
  
---
 
8. Differentiate `dependencies` and `devDependencies` in the `package.json` file?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

In `package.json`, regular `dependencies` are packages that are required for your production-ready site or app to work. Production-ready means the online version of your website or app that the audience experiences.

`devDependencies` are packages used for development purposes, e.g for running tests or transpiling your code.

</blockquote>
</details>
  
---
 
9. What happens if I run `npm install` in the terminal?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
The 
`npm install` command is used for installing JavaScript packages on your local computer.

</blockquote>
</details>
  
---
 
10. What happens if I run `npm uninstall` in the terminal

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>The 

`npm uninstall` command is used to remove installed npm packages on your computer.

</blockquote>
</details>
  
---
 
11. Differentiate between the `npm update and `npm update -g` commands?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

The `npm update command is used to update the node package manager to the latest version.
  
It will also install missing packages.

If the -g flag is specified, this command will update globally installed packages.

If no package name is specified, all packages in the specified location (global or local) will be updated.
  
</blockquote>
</details>
  
---
 
12. What happens if I run `npm init` in the terminal?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

The `npm init` command in the JSON language creates a package.json file for your project’s front end. 

</blockquote>
</details>
  
---
 
13. Can I run the angular application using the `npm start` command?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
<details>
<summary><b>Show Answer</b></summary>
<blockquote>

 Yes, it can run an angular application.

</blockquote>
</details>
  
---
 
14. Why do we need a `package.json` file?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`package.json` contains just JSON. The main purpose of this file is to hold various metadata related to the project. The file is used to provide the information to the node package manager (NPM) that allows identifying the project and its dependencies.

</blockquote>
</details>
  
---

15. Where you can find the `package.json` file?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

The `package.json` file is normally present in the root directory of a project folder structure.

</blockquote>
</details>
  
---

1. Consider there is a variable `name = "Angular"` in `app.component.ts, how can I print this value in template.

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Using String Interpolation, we can print the `name` in the template. In `app.component.html`, 
```html
{{ name }}
```

</blockquote>
</details>
  
---
 
2. Design the angular app with the following criteria
	- Template should have a button named `Click Me`
	- When the user clicked on the button, you should greet the user with the message "Welcome to my angular app"

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

In `app.component.html`, create a button and have `Click Me` enclosed with the `<button>` tag. When the user clicked on the button, we should greet the user with the message "Welcome to my angular app". We need data binding. 
	
```html
<button (click)="onClick()"> Click Me</button>	
```

</blockquote>
</details>
	
--- 
	
3. What are the ways of data binding in angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- Databinding is a technique used to bind the data from a view to a component or from a component to a view.
- They are 1-way data binding and 2-way data binding

![image](https://user-images.githubusercontent.com/70228962/186710327-e17f9bca-c65d-4957-a43a-ddecbd339ee6.png)

</blockquote>
</details>
	
--- 

4. What is Property Binding? How do you achieve it in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
	
- From Component to the view
- Bind values to the attributes of HTML elements.
- Uses [], square brackets in the HTML file
- Create a variable in the class and bind that value to an attribute for the HTML tag

![image](https://user-images.githubusercontent.com/103101208/185592858-66cc92f3-feca-436e-87cf-766c692a8a8c.png)

</blockquote>
</details>
	
--- 

5. How do you achieve event binding in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- From view to component
- Bind DOM events such as keystrokes, button clicks, mouseovers, touches, etc. to a function in the component.
- Uses (), parentheses in the HTML file
- Here, we were calling the `OnClick()` function, when the ‘Click Here’ button is clicked.

![image](https://user-images.githubusercontent.com/103101208/185593164-aa23c1a2-497c-4906-8b32-15af3231d0a6.png)

</blockquote>
</details>
	
--- 

6. What is meant by String Interpolation?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- From the component class to the HTML template
- Uses {{}}, double curly braces in the HTML

![image](https://user-images.githubusercontent.com/103101208/185593247-f546704d-d3ed-4a80-8ff3-01289401fe00.png)

</blockquote>
</details>
	
--- 


7. Do you know about two-way data binding in angular? If so, explain.
	
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
	
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>

- Two-way data binding is achieved by combining property binding and event binding.
- Mostly used in forms.
- Angular uses the `ngModel` directive to achieve two-way binding on HTML `<form>` elements.
- To use the `ngModel` directive, we need to import the `FormsModule` package into our Angular module.
- Here, we enclose the `ngModel` directive within [()]

![image](https://user-images.githubusercontent.com/103101208/185593434-3e70965a-c750-4bbd-aa3b-b3fea6fccba7.png)

</blockquote>
</details>
	
--- 

8. What is the difference between property and attribute in angular?

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
For example, if we take below `<input>` tag:	
	
```html
<input type="text" id="name" value="John">
```
	
Here we have an `<input>` tag set value as "John". It's the initial value.  

In the console of a browser if we execute,
	
```js	
name.getAttribute('value') //attribute value gives John

name. value  // property value also gives John
```
	
Let's say the user enters/changes to  "Jim" in this input textbox.
	
```js
name.getAttribute('value') // attribute value gives Jim

name.value  // property value also gives Jim	
```
**NOTE:** Attributes initialize DOM properties. Once initialization is complete attribute job is done. Properties value can change whereas attribute value cannot change
	
</blockquote>
</details>
  
---

1. What are directives?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
Directives add behavior to an existing DOM element or an existing component instance.
  </blockquote>
</details>
  
---

2. What are the differences between Component and Directive?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

On a short note, A component(`@Component`) is a directive-with-a-template. Some of the major differences are mentioned in a tabular form:

| Component                                                             | Directive                                                     |
|-----------------------------------------------------------------------|---------------------------------------------------------------|
| To register a component we use @Component meta-data annotation        | To register directives we use @Directive meta-data annotation |
| Components are typically used to create UI widgets                    | Directive is used to add behavior to an existing DOM element  |
| Component is used to break up the application into smaller components | Directive is used to design re-usable components               |
| Only one component can be present per DOM element                     | Many directives can be used per DOM element                   |
</blockquote>
</details>
  
---

3. What are the different types of directives in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)
  
<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
    
 - **Component Directives** - Component directives alter the details of how the component should be processed, instantiated, and used at runtime.
- **Structural Directives** -  Structural directives are used for adding, removing, or manipulating DOM elements.
- **Attribute Directives** - Attribute directives are used to change the look and behavior of the DOM elements.
    
<i>Custom Directive: Custom directive can also be created if any of the above directives does not solve our purpose for the requirement</i>

</blockquote> 
</details>
	
--- 
    
4. Explain Structural Directives in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
 <blockquote>
    
- Structural directives are used for adding, removing, or manipulating DOM elements
- Structural directives start with an asterisk (*) followed by a directive name. 
- There are three built-in structural directives - `ngIf`, `ngFor` and `ngSwitch`.
- The `ngFor` directive is used to repeat a part of the HTML template once per each item from an iterable list.
- `ngIf` directive allows us to add or remove DOM Elements based on the Boolean expression. We can also have an else block associated with a ngIf directive.

```html
<div *ngIf=" a > b ; else elseBlock1">
	    {{ a }} is greater than {{ b }}
</div>
<ng-template #elseBlock1>
	    {{ b }} is greater than {{ a }}
</ng-template>
```
- `ngSwitch` directive lets you hide/show HTML elements depending on an expression. `NgSwitchCase` displays its element when its value matches the switch value. `NgSwitchDefault` displays its element when no sibling `NgSwitchCase` matches the switch value.
    
```html
<!-- user to enter any vowels(a, e, i o, u), print any word starting with vowels -->
<input type="text" [(ngModel)]="str" />
<div [ngSwitch]="str">
	    <div *ngSwitchCase="'a'">Entered a!! Word: Apple</div>
	    <div *ngSwitchCase="'e"> Entered e!! Word: Egg</div>
	    <div *ngSwitchCase="'i'"> Entered i!! Word: Ice cream</div>
	    <div *ngSwitchCase="'o'"> Entered o!! Word: Orange</div>
	    <div *ngSwitchCase="'u'"> Entered u!! Word: Umberalla</div>
	    <div *ngSwitchDefault> You Entered Constant </div>
</div>   
```
  
</blockquote> 
</details>
	
--- 
  
5. Explain Attribute Directives in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary> <b>Show Answer</b></summary>
<blockquote>
    
- Attribute directives are used to change the look and behavior of the DOM elements.
- Attribute directives are enclosed with the [] square brackets
- There are two built-in attribute directives - `ngClass` and `ngStyle`
- The `ngClass` directive is used for adding or removing the CSS classes on an HTML element. It allows us to apply CSS classes dynamically based on expression evaluation.
    
```html
    
<h3 [ngClass]="'red'"> Need your attention</h3>
<div [ngClass]="['red','size20']"> Red Background, Text with Size 20px </div>
<div [ngClass]="{'red':false,'size20':true}">Text with Size 20px</div>

```
- The `ngStyle` directive allows us to dynamically change the style of the HTML element based on the expression.
    
```html
Enter the username: <input type='text' [(ngModel)]='name'>
<div [ngStyle]="{'background-color':username === 'Admin' ? 'green' : 'red' }"></div>
```

</blockquote> 
</details>
	
--- 

6. Design the angular app with the following criteria
    - Get the `name` and `age` from the user
    - If entered `age`is greater than 60, print their `name` then say "is a senior citizen"
    - Else, their `name` then say "is not a senior citizen"

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

**Steps:**
1. Create an angular project by running the `ng new angularDemo2` command in the angular CLI
2.In the `app.component.html` file, create a form to get the `name` and `age` from the user
```html
Name: <input type="text" [(ngModel)]="name" /> <br> 
Age: <input type="text" [(ngModel)]="age" />
```
3. In the `app.component.ts` file, create a `name` and `age` variables.
```ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'angularDemo2';

  name !: string;
  age !: number;
}	
```
4. Since we are using the `ngModel`directive, we have to import `FormsModule` in the `app.module.ts` file.
```java
 imports: [
    BrowserModule,
    FormsModule
 ]
```
5. To check entered age and print the sentence according to it. We need to use the `ngIf` directive. In the `app.component.html` file,
```ts
<div *ngIf=" age > 60; else elseBlock1">
    {{name}} is a senior citizen
</div>
<ng-template #elseBlock1>
    {{name}} is not a senior citizen
</ng-template>	
```
6. Launch the application by running `ng serve -o` command.
7. Now, able to see the excepted output.
![image](https://user-images.githubusercontent.com/70228962/186344357-656f9e28-3cfa-4dc0-9873-dbd62dcd14d8.png) 

![image](https://user-images.githubusercontent.com/70228962/186344483-f0368ed8-f0e2-46ec-8b3e-42e4cc6eb2c1.png)

</blockquote>
</details>

---

7. Design angular application with the following criteria
	-  Get a number from the user. 
	-  Print it as an even number or an odd number

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
1. Create an angular project by running `ng new angularDemo2` command in the angular CLI
2. In the `app.component.html` file, create a form to get the `name` and `age` from the user
```html
Enter a number: <input type="text" [(ngModel)]="num" />
```
3. In `app.component.ts` file, create a `name` and `age` variables.
```ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'angularDemo2';
	
  num !: number;
}	
```
4. Since we are using the `ngModel`directive, we have to import `FormsModule` in the `app.module.ts` file.
```java
 imports: [
    BrowserModule,
    FormsModule
 ]
```
5. To check entered number is odd and even and print it. We will use the `ngSwitch` directive. In the `app.component.html` file,
```ts
Enter a number: <input type="text" [(ngModel)]="num">

<div ngSwitch="{{num%2}}">
    <div *ngSwitchCase="'0'">{{num}} is even.</div>
    <div *ngSwitchCase="'1'">{{num}} is odd</div>
    <div *ngSwitchDefault>Nothing Found</div>
</div>
```
6. Launch the application by running `ng serve -o` command.
7. Now, able to see the excepted output.

![image](https://user-images.githubusercontent.com/70228962/186347155-19484af6-e1f9-4818-bb4d-ba6d47864fb2.png)

![image](https://user-images.githubusercontent.com/70228962/186347246-414044f8-21bf-4021-a3c4-b2dba0540442.png)

</blockquote>
</details>
  
---

8. How do you create a custom directive in Angular?
 
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Steps to creating custom directive in angular:
	
1. To create an angular application, run `ng new myapp` command.
2. Then, we can create a directive by running the `ng g d myHighlight` command. Angular CLI creates two files `my-highlight.directive.spec.ts` and `my-highlight.directive.ts` and updates `app.module.ts`
3. In `my-highlight.directive.ts`, we will create an instance of `ElementRef` and just high lighting the background color as yellow.
```ts
import { Directive, ElementRef} from '@angular/core';

@Directive({selector: '[myHighlight]'})
export class MyHighlightDirective {
  constructor( private el: ElementRef) {
    el.nativeElement.style.backgroundColor = 'yellow';
   }
}
```
4. Now this directive extends HTML element behavior with a yellow background as below
```html
<p myHighlight> Hi, there!!</p>	
```
5. Launch the angular application by running `ng serve -o` command.  The expected output will be,
	
![image](https://user-images.githubusercontent.com/70228962/186374096-514930ba-f29c-424e-bcf8-11318b5c0734.png)

</blockquote>
</details>
  
---

9. What's Angular `ElementRef`?
 
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
Angular `ElementRef`is simply a class that wraps native DOM elements in the browser and allows you to work with the DOM by providing the native elements` object which exposes all the methods and properties of the native elements.

</blockquote>
</details>
  
---

10. How do you choose an element from a component template?
	
![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)
	
<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
To directly access items in the view, use the `@ViewChild` directive. Consider an input item with a reference.
```html
<input #example>
```
	
and construct a view child directive that is accessed in the `ngAfterViewInit` lifecycle hook
```ts		
@ViewChild('example') input;

ngAfterViewInit() {
  console.log(this.input.nativeElement.value);
}
```	
	
</blockquote>
</details>
  
---

11. What is `ng-template` in Angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`ng-template` is an Angular element that is used for rendering HTML in a template. However, it is not rendered directly on DOM. If you include an ng-template tag to a template, the tag and the content inside it will be replaced by a comment upon rendering.

</blockquote>
</details>
  
---
 
12. Create a `myHighlight` attribute directive to set an element’s background color when you hover over that element.

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
	
1. To create an angular application, run `ng new myapp` command.
2. Then, we can create a directive by running `ng g d myHighlight` command. Angular CLI creates two files `my-highlight.directive.spec.ts` and `my-highlight.directive.ts` and updates `app.module.ts`
3. In `my-highlight.directive.ts`, we will create an instance of `ElementRef` and highlighting based on the mouseover and mouseleave.
```ts
import { Directive, ElementRef, HostListener } from '@angular/core';

@Directive({
  selector: '[myHighlight]'
})
export class MyHighlightDirective {

  constructor(private el : ElementRef) {}

  @HostListener('mouseover') onMouseOver() {
    this.changeBackgroundColor('blue');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.changeBackgroundColor('white');
  }

  private change background color(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }

}
```
4. Adding the `myHighlight` directive to the HTML elements, will change color based on mouseover and mouse leave
```html
<p myHighlight> Hi, there!!</p>	
```	
5. Launch the angular application by running `ng serve -o` command. Then, we'll able to see the excepted output

![image](https://user-images.githubusercontent.com/70228962/186696341-de34b3a7-9c4a-4102-8d9d-16d6984d4746.png)
	
</blockquote>
</details>
  
---

1. What are Pipes in angular? Explain with an example. 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Pipes provide a way to transform values in an Angular template. Pipes are used with a Pipe (`|`) character, and take integers, strings, arrays, and dates as input and return a desired formatted output which can be displayed in the browser.
    
For example, a Date object shows the date in this format: `Sat Aug 03 2019 19:48:11 GMT+0530 (India Standard Time)` which is not easy for normal users to understand. It’s better to have the date in this format `Saturday, 03 Aug 2019 07:50 PM`. This can be achieved using pipes.

</blockquote>
</details>
  
---
 
2. How you can transform any strings, currency amounts, dates, and other data for display?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Using Pipes, we can transform any strings, currency amounts, dates, and other data for display.

</blockquote>
</details>
  
---
 
3. What happens if I decorate the class with a `@Pipe` decorator?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

If we want to create a custom pipe in angular, we need to annotate the class with the `@Pipe` decorator.

The `@Pipe` decorator has a name property, which is used to specify the name of the pipe. 
  
</blockquote>
</details>
  
---
 
4. What do you get from the below code?
```ts
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({
  name: 'filter'
})
export class FilterPipe implements PipeTransform {
  transform(array: string[], startWith: string): any {
    let temp: string[] = [];
    temp = array.filter(a => a.startsWith(starts with));
    return temp;
  }
}
```
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>
    
- `FilterPipe` is a custom pipe.
- We take an array of strings (`array`) and another string (`startWith`) as input.
- Using the `filter` method, we only filter a string that starts with a value in `starts with` and returns it.
    
</blockquote>
</details>
  
---
 

5. Can we create our pipe in angular? If so, how?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)


<details>
<summary><b>Show Answer</b></summary>
<blockquote>
  
 Yes, we can our own pipe in angular. 
  
**For example:** we create a custom pipe to get the first character in a given string, by running the `ng g pipe firstChar` command in the terminal. The CLI creates 2 files - `first-char.pipe.spec.ts` and `first-char.pipe.ts` under the _src/app_ folder and updates the `app.module.ts` file.

In the `first-char.pipe.ts` file, we write the logic for returning the first character in a given string.
  
```ts
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({   name: 'firstChar' })
export class FirstCharPipe implements PipeTransform {

  transform(value: string): string{
    return value[0];
  }
}  
```
And, we can use any template file. For example,  in the `app.component.ts` file,
  
```ts
{{ "Hello World" | firstChar}}  
```

</blockquote>
</details>
  
---
 
6. Design the angular application to print the current date in this format "MM/dd/yy".

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

We can use date pipe to date in this format "MM/dd/yy". Also, we can get the current date using `Date. now()`.

![image](https://user-images.githubusercontent.com/70228962/186723294-69118376-7c4a-48e5-966f-c8cd0ba50954.png)

**NOTE:**  Output will be like  _08/25/22_
    
</blockquote>
</details>
  
---
 
7. Design the angular application to get a sentence from the user and print the count of words in the given sentence.

![Medium](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/Medium%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

1. Create an angular application by running `ng new myapp` command 
2. Create a custom pipe to count words by running the `ng g pipe wordcount` command
3. In the `wordcount.pipe.ts` file, write the logic for word count
```ts
import { Pipe, PipeTransform } from '@angular/core';
@Pipe({   name: 'wordcount' })
export class WordcountPipe implements PipeTransform {
  transform(value : string): unknown {
    return value.trim().split(' ').length;
  }
}
```
4. In `app.component.html`, get the sentence and use the `wordcount` pipe. Also, we have to import `FormsModule` in the `app.module.ts` and create a `sentence` variable of type `string` like `sentence !: string` in the `app.component.ts`.
    
```ts
<p>Enter a sentence: <input type="text" [(ngModel)]="sentence"> <br/></p>

{{ sentence | wordcount}}
```
5. Output will be
    
![image](https://user-images.githubusercontent.com/70228962/186726853-a751b72f-faf3-4a00-ad1a-5b43176b0ae5.png)

</blockquote>
</details>
  
---
 
8. Design the angular application to print the list of groceries items followed by their price in rupees

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

For example, below are the groceries items and its cost.
```ts
    items = [
    { name : "Pasta" ,  cost: 32 },
    { name : "Rice" ,  cost: 50 },
    { name : "Milk" ,  cost: 30 },
    { name : "Egg" ,  cost: 5}
  ]
```
    
 To print the list of groceries items followed by their price in rupees, we just need to use the `ngFor` directive and `currency` pipe
 
```html
 <div *ngFor="let item of items">
    <li> {{item.name}} - {{ item.cost | currency:'INR'}}</li>
</div>
 ```

The output will be like
   
![image](https://user-images.githubusercontent.com/70228962/186734281-ebe35c70-f152-402b-9e36-8b3a48f9ff90.png)


</blockquote>
</details>
  
---
 
9. How can slice the strings?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

 For example,
 ```html
<p>{{ "abcdefghijk" | slice:3:7}}  </p>
<!-- output: 'defg' -->
```

We have a slice pipe in angular to slice the strings. Here, a number is given per character to our input string to understand the start and end index. The index starts from 0.
    
```
 0   1   2   3   4   5   6   7   8   9   10 
 |   |   |   |   |   |   |   |   |   |   |    
 a   b   c   d   e   f   g   h   i   j   k
 ```
In our example, we have the following indexes. 
    
start = 3
    
end = 7
    
Slice pipe will return substring starting from index 3 i.e character d and will include all characters before index 7 i.e up to g. The character at the end index will not be included in the output substring.

</blockquote>
</details>
  
---
 
10. List some of the built-in pipes in angular. 

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

Some of the built-in pipes are:

- **Date pipe**: Used for formatting dates.
- **Decimal pipe**: Used for formatting numbers
- **Currency pipe**: Used for formatting currencies
- **Lowercase pipe**: Used for converting strings into lowercase.
- **Uppercase pipe**: Used for converting strings into uppercase.
    
**For example:**
```html
<h2>Built-in Pipes</h2>
<li>{{"Pipes"}} </li>
<li>{{"Pipes" | uppercase}}</li>
<li>{{"Pipes" | lowercase}} </li>
<li>{{dob}}</li>
<li>{{dob | date}}</li>
<li>{{dob | date |uppercase }}</li>
<li>{{17.81922 | number }}</li>
<li>{{17.819227546354 | number: '3.4-6' }}</li>
<li>{{17.81922 | number : '2.0-0'}}</li>
<li>{{365778 | currency}}</li>
<li>{{365778 | currency: 'INR'}}</li>
```
    
 Output:
 
![image](https://user-images.githubusercontent.com/70228962/186727762-9ca23c43-6cb0-4026-a00d-c443324950ee.png)  
    
</blockquote>
</details>
  
---

11. Design the angular application to print the user's birthday in this format "MAY 19, 1997".
 
![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

1. Create an angular application by running `ng new myapp` command 
2. In `app.component.html`, get the user's birthdate. Also, import `FormsModule` in the `app.module.ts` and create a `birthdate` variable of type `number` like `birthday !: number;` in the `app.component.ts`.
 ```html
 <p>Enter your birthday: <input type="date" [(ngModel)]="birthday"> <br/></p>

<p>Date Of birth : {{ birthday | date | uppercase}} </p>
<!-- OUTPUT Date Of birth : MAY 19, 1997 -->  
 ```
   
 Here we're chaining pipes, chaining the `date` pipe and `uppercase` pipe. If, we just have only date pipe `{{ birthday | date }}` the output will be like `Aug 3, 2022`. Since the excepted output has Month is in uppercase, there is a need to transform month to uppercase. so will chain the uppercase pipe after the date pipe. 

</blockquote>
</details>
  
---

12. What is the use of `PipeTransform` in angular?

![Easy](https://github.com/revaturelabs/interviewquestions/blob/dev/ComplexityTags/simple%20(2).svg)

<details>
<summary><b>Show Answer</b></summary>
<blockquote>

`PipeTransform` is an interface that is implemented by pipes to perform a transformation. Angular invokes the `transform` method with the value of a binding as the first argument, and any parameters as the second argument in list form.
    
```ts
interface PipeTransform {
  transform(value: any, ...args: any[]): any
}
```
</blockquote>
</details>
  
---
