## Angular
* Angular front-end development framework.
* For developing Single Page Application.
* Developed by Google.
* MVC Framework.
* Open source.
* Use NPM and Command Line Interface(CLI).
* First released in 14th Sept 2016.

## Angular Vs Angular Js
* Angular Js is Oldest version not in use now.
* Latest version after version 2.
* Angular is re-written version, structure and upgraded framework.

## Setup and Installation
* Install Node and NPM.
* Install Angular CLI.
* Angular CLI command: npm install -g @angular/cli
* Use command: ng version - to check Angular version
* Install particular Angular version: npm install -g@angular/cli@10.0.0 (in CLI).
* Manage Node Js version command: nvm.

## Files and Folder Structure
1. Important file and folder for begineers:

    * package.json - Most important file, contains project details.
    * node_modules - Contains all libraries. Never mess with this file.
    * src folder - Most important folder, all development work is done inside this folder. app - is a component.
    * assests - Contains extra images, css etc.
    * environments - Essential for deployment.
    * index.html - First file to load.
    * main.js - Bootstrap(connects) html & angular.
    * style.css - Global css.

2. Important file and folder for advance:

    * package-lock.json - Carries details of all packages and the internal dependencies required by those packages.
    * angular.json - Application configuration file(like which file to load first, by default css file, etc).
    * tsconfig files - Configuration of typescript.
    * .browserslistrc - Details about which browsers application support.
    * karma.config.js - Test file configuration.
    * polyfill.ts - Used to add libraries to run application appropriately in browser.
    * .editorconfig - IDE configuration.

## Apply First Change in Angular App
* index.html - Starting project file.
* app.component.html - File inside <b>app</b> folder. Contain html code to display in web-page.<br>
    Eg:
    ```html
    <!-- Inside app.component.html file -->
    <h1>Hello {{title}}!</h1>
    <!--{{title}} - TypeScript code from app.component.ts file -->
    ```

## What is Interpolation?
### Interpolation
* Used to display dynamic data inside html page.<br>
    Eg:
    ```html
    <!-- Inside app.component.html file -->
    <h1>Hello {{title}}!</h1>
    <!--{{title}} - TypeScript code from app.component.ts file -->
    ```
* Dynamic data(inside app.component.ts file) as the data can be retrived from some logical calculation, API or some other component.<br>
    Eg:<br>
    Inside HTML
    ```html
    <h1>Hello {{title}} !</h1>
    <h2>{{getValue()}}</h2>
    ```
    Inside TypeScript
    ```typescript
    import { Component } from '@angular/core';

    @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.css']
    })
    export class AppComponent {
    title = 'blog';
    getValue() {
    return "Get function data."
    }
    }
    ```
    Web Page
    
    ![Alt text](Interpolation-web-page.png)
* Can also perform arithmetic/logical operations using interpolation.<br>
    Eg:<br>
    Inside HTML
    ```html
        <h2>2+2</h2>
    ```
    Web Page
    ![Alt text](Interpolation-logical.png)
* Things we cannot perform using Interpolation:<br>
    1. Inside HTML<br>
        ```html
            <h1>{{title = "Web App"}}</h2>
            var++;
            <!-- Failed to Compile -->
        ```
        Also cannot increment, decrement, new keyword, assignment operator, typeOf etc.
* Can add class using HTML.
    ```html
        <h1 class={{title}}>Hello world!</h1>
    ```

## Angular CLI & Important Commands
* With the help of CLI we generate components, add config, build app, generate modules, services etc.
* CLI makes it easier for us to create files/folders required for our project.
* Use command <i>ng help</i> to list all commands.
* src/app(root folder) - Contains all components.
* Generate component:
```
// In cmd
> ng generate component component_name
// In short form
> ng g c component_name

```
* Inside a component:
![Alt text](component-file-structure.png)
    1. .css - For style.
    2. .html - structure of web page.
    3. spec.ts - For testing.
    4. .ts - TypeScript for logic.
In single line component, only one file is cretaed.

* Module Vs Component:<br>
    1. Module is more complex and adds bigger functionality.
    Eg: 
        ```
            > ng g m user-auth
            > ng g c user-auth/sign-in 
        ```
        Module can contain components.
    2. Component is simpler.
* To build project:
    ```
        > ng build
        // above command creates a dist\project_name
    ```
    We put the generated folder into the server to deploy our project.

## Component
* Component is a building block for creating some functionality/feature.
* Building block of website for a particular feature.
* Command:
    ```
    > ng g c component_name
    ```
* Inside app.module.ts the component gets automatically import.<br>
    Eg:
    ```typescript
        // Here we used > ng g c user-list to generate UserListComponent
        import { NgModule } from '@angular/core';
        import { BrowserModule } from '@angular/platform-browser';

        import { AppComponent } from './app.component';
        import { UserListComponent } from './user-list/user-list.component';

        @NgModule({
        declarations: [
            AppComponent,
            UserListComponent
        ],
        imports: [
            BrowserModule
        ],
        providers: [],
        bootstrap: [AppComponent]
        })
        export class AppModule { }
    ```
* To use the component:<br>
    Eg:<br>
    Inside .html:
    ```html
        <!-- Inside app.component.html, 
        add the component selector 
        inside component-name.component.ts
        ad html tag -->

        <!-- Inside app.component.html -->
        <app-user-list></app-user-list>

    ```
    Inside component's typescript file:
    ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-user-list', // Use this as html tag to use the component
        templateUrl: './user-list.component.html',
        styleUrls: ['./user-list.component.css']
        })

        export class UserListComponent {}
    ```
* We can use component selector inside same html file multiple times.
* We can also change the name of selector inside .ts file and use the changed name.
* Making separate component for each feature is a good practice.

## Component with Inline Style & Template
* Inline style command:
    ```
    >ng g c component_name --inline-style
    
    <!--
        * Above command will generate 
        component without .css file
        * Here, we write the css inline 
        inside .ts file
        * The css code goes inside 
    -->
    ```
    .ts file:
    ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-user-list',
        templateUrl: './user-list.component.html',
        styles: [ 
            `.custom{
            color: red;
            }`
        ]
        })
        export class UserListComponent {}
    ```
* Inline template command:
    ```
    >ng g c component_name --inline-template
    <!--
        * Above command will generate 
        component without .html file
        * Here, we write the html inline 
        inside .ts file
        * The html code goes inside 
    -->
    ```
    .ts file:
    ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-student-list',
        // html code goes here
        template: ` 
            <p>
            student-list works!
            </p>
        `,
        styleUrls: ['./student-list.component.css']
        })

        export class StudentListComponent {}
    ```
* Inline style and Inline template (together) command:
    ```
        > ng g c component-name --inline -style --inline -template
        <!-- 
            * Here only .ts file is generated.
            * Write html and css both inside .ts file
         -->
    ```
    .ts file:
    ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-country-list',
        template: `
            <p>
            country-list works!
            </p>
        `,
        styles: [`
            p{
            color: blue;
            }
        `
        ]
        })
        export class CountryListComponent {}
    ```

## Module
 ![Alt text](module.jpg)
 * Create module command:
    ```html
    <!-- Generate module -->
    > ng g m module-name
    <!-- Generate component inside module -->
    > ng g m module-name/component-name
    ```

 * app.module.ts:
    ```typescript
        import { NgModule } from '@angular/core';
        import { BrowserModule } from '@angular/platform-browser';

        // To use module, here UserAuthModule is a custom module
        import { UserAuthModule } from './user-auth/user-auth.module'

        import { AppComponent } from './app.component';

        @NgModule({
        // store components/services here, separated by commas
        declarations: [
        AppComponent
        ],
        // store modules here, separated by commas
        imports: [
        BrowserModule
        ],
        providers: [],
        bootstrap: [AppComponent]
        })
        export class AppModule { }
    ```
* To use our module, we have to import it inside the app.module.ts file.<br>
    i. We need to export it in the module's .ts file.
    Eg:<br>
    ```typescript
        import { NgModule } from '@angular/core';
        import { CommonModule } from '@angular/common';
        import { LoginComponent } from './login/login.component';

        @NgModule({
        declarations: [
        LoginComponent
        ],
        imports: [
        CommonModule
        ],
        exports: [
        LoginComponent
        ]
        })
        export class UserAuthModule { }
    ```
## Make and call function on button click
* Create function inside app.component.ts file.<br>
    Eg:
    ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
        })
        export class AppComponent {
        [x: string]: any;
        title = 'blog';

        getName() {
        alert('Function called!');
        }

        getNameParam(name:string, age:number) {
        alert("Hello " + name + "Age: " + age);
        }
        }
    ```
* To call the function in .html of the project.
    Eg:
    ```html
        <button (click)="getName()">Click Me</button>
        &nbsp;
        <button (click)="getNameParam('Smith',15)">Submit</button>
    ```
* Why data-type is now essential in latest version of Angular?<br>
 => Because, inside tsconfig.json file the strict: true. Earlier it used to be strict: false.

## Events
Event binding lets you listen for and respond to user actions such as keystrokes, mouse movements, clicks, and touches.<br>
Eg:<br>
Inside app.component.ts:
```typescript
    import { Component } from '@angular/core';

    @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
    })
    export class AppComponent {
        [x: string]: any;
        title = 'blog';

        getData(val:string) {
            console.warn(val); // static
        }
    } 
```
Inside app.component.html:
```html
    <button (click)="getData('')">Call Function</button> <br>
    &nbsp;
    <!-- id_name can be anything -->
    <input type="text" #id_name (keyup)="getData(id_name.value)" placeholder="Event keyup">
    &nbsp;
    <input type="text" #id_1 (keydown)="getData(id_1.value)" placeholder="Event keydown">
    &nbsp;
    <!-- as soon as we shift focus from the box(i.e move cursor away) input gets recorded -->
    <input type="text" #id_2 (blur)="getData(id_2.value)" placeholder="Event blur">

    &nbsp;
    <input type="text" #id_3 (input)="getData(id_3.value)" placeholder="Event input">

    <br>
    <h1 type="text" #id_4 (mouseover)="getData('over')">Hello</h1>
```
Output:<br>
(keyup)
![Alt text](event.png)
(keydown)
![Alt text](event-keydown.png)
(blur)
![Alt text](event-blur.png)
(mouseover)
![Alt text](event-mouseover.png)

## Get Text Box Value And Print

Eg:<br>
* Step 1: Inside app.component.ts create function you want to perform, here we have getValue() function:
    ```typescript
        import { Component } from '@angular/core';
        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            [x: string]: any;
            title = 'blog';

            displayVal:string ='';

            getValue(val: any) {
                console.warn(val);
                this.displayVal = val;
            }
        }
    ```
* Step 2: Inside app.component.html use html tag id to display value entered inside input tag:
    ```html
    <input type="text" #id_0 placeholder="Enter Name" name="name">
    <br>

    <!-- to get value typed in input box -->
    <button (click)="getValue(id_0.value)">Click</button>

    <!-- to get name of input box -->
    <button (click)="getValue(id_0.name)">Click</button>

    <p>{{displayVal}}</p>
    ```
* Output:
![Alt text](get-input-box-value-display.png)

## Make Counter (assignment)
* Make a counter front-end app to increment/decrement value:<br>
    1. Inside app.component.ts:
        ```typescript
        import { Component } from '@angular/core';

        @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
        })
        export class AppComponent {
        [x: string]: any;
        title = 'blog';

        count = 0;

        counter(operator:string) {
            operator === '++' ? this.count++:this.count--;
        }
        }
        ```
    2. Inside app.component.html:
        ```html
        <button (click)="counter('--')">--</button>
        &nbsp;
        <button (click)="counter('++')">++</button>
        <br>
        <p>Count value: {{count}}</p>
        ```
    3. Output:
        ![Alt text](counter-assignment.png)

## Basic Rule of Style
* <b>Component Style</b>: To change css of particular component then change in its specific .css file.
* <b>Global Style</b>:To change css of component thoughout the project(say h1-tag across the project), then make changes in the style.css file(global css).
* <b>Internal Style:</b> Write css in html file within < style> css code goes here< /style> tags.
* Internal style > Component Style > Global Style <= in terms of priority.

## Property Binding
Property binding in Angular helps you set values for properties of HTML elements or directives. Use property binding to do things such as toggle button features, set paths programmatically, and share values between components.

* Difference between Property Binding and Interpolation:<br>
Eg:
    1. Syntax:
    ```html
    <!-- Interpolation -->
    <input type="text" name="user-name" value="{{name}}">
    <br>
    <!-- Property Binding -->
    <input type="text" name="password" [value]="name">
    ```
    2. Differences: Cannot treat boolean values.<br>
        Html:
        ```html
        <!-- Interpolation -->
        <input type="text" name="user-name" value="{{name}}" disabled="{{disable}}">
        <br>
        <!-- Property Binding -->
        <input type="text" name="password" [value]="name" [disabled]="disable">

        ```
        TypeScript:
        ```typescript
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            [x: string]: any;
            title = 'blog';
            name = "Ram";
            disable = false;
        }
        ```
        The web-page does not respond accordingly. input-tag remain disabled though value set is false, if we use interpolation.

        Output:
        ![Alt text](property-binding.png)
    3. Exercise: Check using buttons.<br>
        Eg:<br>
        * app.component.html:
            ```html
            <!-- interpolation -->
            <button  disabled="false" (click)="display()">Not Works!</button>
            &nbsp;
            <!-- process binding -->
            <button [disabled]="false" (click)="display()">Works!</button>

            <p>Display: {{displayVal}}</p>
            ```
        * app.component.ts:
            ```typescript
            import { Component } from '@angular/core';

            @Component({
                selector: 'app-root',
                templateUrl: './app.component.html',
                styleUrls: ['./app.component.css']
            })
            export class AppComponent {
                [x: string]: any;
                title = 'blog';
                name = "Ram";
                disable = false;

                displayVal = '';
                display() {
                    this.displayVal = 'Namaste!!!';
                }
            }
            ```
        * Output: Despite disabled="false", input-tag that uses interpolation does not work properly.
        ![Alt text](interpolation-vs-propertyBinding.png)

## If-Else Condition
* Inside app.component.html:
    ```html
    <h1 *ngIf="show; then ifBlock else elseBlock"></h1>
    <!-- we can also compare strings to check -->
    <h1 *ngIf="show == 'yes'; then ifBlock else elseBlock"></h1>

    <ng-template #ifBlock>
        <h1>If Condition</h1>
    </ng-template>

    <ng-template #elseBlock>
        <h1>Else Condition</h1>
    </ng-template>
    ```
* Inside app.component.ts:
    ```typescript
    import { Component } from '@angular/core';

    @Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
    styleUrls: ['./app.component.css']
    })
    export class AppComponent {
    [x: string]: any;
    title = 'blog';
    show = true;
    show_1 = 'yes'; // we can also compare strings
    }
    ```
* Output: As show is set true, ifBlock gets executed.
* *ngIf vs [ngIf]:
    ![Alt text](ngIf-vs-%5BngIf%5D.png)

## Multiple condition or else if
* In angular we only have *ngIF / [ngIf], we do not have else-if/ else.
* Eg:<br>
    * Inside app.component.html:
        ```html
        <!-- below code prints color based on input -->
        <input #input_id type="text" placeholder="Enter color">
        &nbsp; &nbsp;
        <button (click)="getColor(input_id.value)">Submit</button>
        <br>

        <!-- multiple else conditions -->
        <ng-template [ngIf]="color === 'red'">
            <h1 style="color: red;">Red</h1>
        </ng-template>
        <ng-template [ngIf]="color === 'blue'">
            <h1 style="color: blue;">Blue</h1>
        </ng-template>
        <ng-template [ngIf]="color === 'green'">
            <h1 style="color: green;">Green</h1>
        </ng-template>
        ```
    * Inside app.component.ts
        ```typescript
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            [x: string]: any;
            title = 'blog';
            color = '';

            getColor(colorVal: string) {
                if(colorVal === 'red')
                this.color = colorVal;
                else if(colorVal === 'blue') {
                this.color = colorVal;
                }
                else 
                this.color = colorVal;
            }
        }
        ```
    * Output:
      ![Alt text](multiple-if-else.png)  

## Switch Case
* If there are many conditions then we prefer to use switch case over if condition.
* Eg:<br>
    * app.component.html
        ```html
        <div [ngSwitch]="color">
            <h1 *ngSwitchCase="'red'" style="color: red;">Red</h1>
            <h1 *ngSwitchCase="'blue'" style="color: blue;">Blue</h1>
            <h1 *ngSwitchCase="'green'" style="color: green;">Green</h1>
            <h1 *ngSwitchCase="'yellow'" style="color: green;">Yellow</h1>
            <h1 *ngSwitchCase="'brown'" style="color: green;">Brown</h1>
            <!-- if no case matches -->
            <h1 *ngSwitchDefault>Unknown Color</h1>
        </div>
        ```
    * app.component.ts
        ```typescript
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
        [x: string]: any;
        title = 'blog';
        color = 'red'; // changeable
        }
        ```
## For Loop
* Eg:
    * Inside app.component.html
        ```html
        <h2>Display users:</h2>
        <p *ngFor="let item of users">{{users.indexOf(item) + 1}}. {{item}}</p>
        <br>
        <h2>Player details: </h2>
        <p *ngFor="let obj of userDetails">{{userDetails.indexOf(obj) + 1}}. {{obj.name}} SR: {{obj.sr}}</p>
        ```
    * Inside app.component.ts
        ```typescript
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            [x: string]: any;
            title = 'blog';
            // array
            users = ['Virat', 'Dhoni', 'Gill', 'Rohit', 'Surya'];

            // array of objects
            userDetails=[
                {name: 'Virat', sr: 135},
                {name: 'Dhoni', sr: 147},
                {name: 'Gill', sr: 143},
                {name: 'Rohit', sr: 153},
                {name: 'Surya', sr: 168}
            ]
        }
        ```
## Nested Loops