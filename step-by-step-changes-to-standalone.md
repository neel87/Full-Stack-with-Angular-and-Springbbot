# ANGULAR STANDALONE COMPONENTS AND MIGRATION STEPS

## Why Angular Standalone Components?
Angular 13 has introduced a novel functionality known as `Angular standalone components`. 
These components streamline the process of Angular development and minimize the need for repetitive code. 
_Unlike conventional Angular modules, you DO NOT need to have `NgModule` files for standalone components._
Consequently, you can effortlessly import and utilize them in any section of an application.

## Benefits
- Improved Developer Experience
- Reduced boilerplate
- Increased modularity
- Improved performance

> [!IMPORTANT]
> If you have you're using Angular <= 17.1.1, please follow the migration steps provided [here](MigrateToAngularStandalone.md)
### Let's start...

# Section3: Getting Hands on With Angular
## 14. Step 09: Change - generated
### frontend/todo/src/app/app.component.ts

### BEFORE 
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  //template: '<h1>{{title}}<h1>',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'todo';
  message = 'Welcome to in28Minutes';
}
```

### AFTER
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  //template: '<h1>{{title}}<h1>',
  styleUrls: ['./app.component.css'],
  standalone: true // Generated - Change
})
export class AppComponent {
  title = 'todo';
  message = 'Welcome to in28Minutes';
}
```
## 15. Step 10: Change - generated, No Update in app.module.ts
### frontend/todo/src/app/welcome/welcome.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-welcome',
  templateUrl: './welcome.component.html',
  styleUrls: ['./welcome.component.css'],
})
export class WelcomeComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```

### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-welcome',
  templateUrl: './welcome.component.html',
  styleUrls: ['./welcome.component.css'],
  standalone: true // Generated - Change
})
export class WelcomeComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```

## 17. Step 12: Change - generated, No Update in app.module.ts
### frontend/todo/src/app/login/login.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css'],
})
export class LoginComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```

### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css'],
  standalone: true // Generated - Change
})
export class LoginComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```
## 21. Step 16: Change - generated, import `NgIf` directive
### frontend/todo/src/app/login/login.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css'],
})
export class LoginComponent implements OnInit {
  username = 'in28minutes'
  password = ''
  errorMessage = 'Invalid Credentials'
  invalidLogin = false
  
  constructor() { }
   
   ngOnInit() {
   }
   
   handleLogin() {
      // console.log(this.username);
      if(this.username==="in28minutes" && this.password === 'dummy') {
        this.invalidLogin = false
      } else {
        this.invalidLogin = true
      }
   }
}
```

### AFTER
```js
import { Component } from '@angular/core';
import { NgIf } from '@angular/common'; // Added

@Component({
  selector: 'app-login',
  templateUrl: './login.component.html',
  styleUrls: ['./login.component.css'],
  standalone: true // Generated - Change
  imports: [NgIf] // Added
})
export class LoginComponent implements OnInit {
  username = 'in28minutes'
  password = ''
  errorMessage = 'Invalid Credentials'
  invalidLogin = false
  
  constructor() { }
   
   ngOnInit() {
   }
   
   handleLogin() {
      // console.log(this.username);
      if(this.username==="in28minutes" && this.password === 'dummy') {
        this.invalidLogin = false
      } else {
        this.invalidLogin = true
      }
   }
}
```

## 22. Step 17: Change - generated
### frontend/todo/src/error/error.component.ts

### BEFORE
```js
import { Component, OnInit } from '@angular/core';

@Component({
    selector: 'app-error',
    templateUrl: './error.component.html',
    styleUrls: ['./error.component.css'],
})
export class ErrorComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```

### AFTER
```js
import { Component, OnInit } from '@angular/core';

@Component({
    selector: 'app-error',
    templateUrl: './error.component.html',
    styleUrls: ['./error.component.css'],
    standalone: true // Generated - Change
})
export class ErrorComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```
## 25. Step 20: Change - generated, No Update in app.module.ts(deleted in standalone)
### frontend/todo/src/list-todos/list-todos.component.ts

### BEFORE
```js
import { Component, OnInit } from '@angular/core';

@Component({
    selector: 'app-list-todos',
    templateUrl: './list-todos.component.html',
    styleUrls: ['./list-todos.component.css'],
})
export class ListTodosComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```
### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component, OnInit } from '@angular/core';

import { NgIf, NgFor, UpperCasePipe, DatePipe } from '@angular/common'; // Added

@Component({
    selector: 'app-list-todos',
    templateUrl: './list-todos.component.html',
    styleUrls: ['./list-todos.component.css'],
    standalone: true, // Generated - Change
    imports: [NgIf, NgFor, UpperCasePipe, DatePipe] // Added
    
})
export class ListTodosComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```
## 26. Step 21: Change - generated
### frontend/todo/src/app/welcome/welcome.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
  selector: 'app-welcome',
  templateUrl: './welcome.component.html',
  styleUrls: ['./welcome.component.css'],
})
export class WelcomeComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```
### AFTER

```js
import { ActivatedRoute, RouterLink } from '@angular/router'; // Added RouterLink
import { Component } from '@angular/core';
import { NgIf } from '@angular/common'; // Added

@Component({
  selector: 'app-welcome',
  templateUrl: './welcome.component.html',
  styleUrls: ['./welcome.component.css'],
  standalone: true, // Generated - Change
  imports: [RouterLink, NgIf] // Added
})
export class WelcomeComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```
## 32. Step 27: Change - generated, No Update in app.module.ts(deleted in standalone)
### frontend/todo/src/app/menu/menu.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
    selector: 'app-menu',
    templateUrl: './menu.component.html',
    styleUrls: ['./menu.component.css'],
})
export class MenuComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```

### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component } from '@angular/core';

@Component({
    selector: 'app-menu',
    templateUrl: './menu.component.html',
    styleUrls: ['./menu.component.css'],
    standalone: true // Generated - Change
})
export class MenuComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```
### frontend/todo/src/app/footer/footer.component.ts

### BEFORE
```js
import { Component } from '@angular/core';

@Component({
    selector: 'app-menu',
    templateUrl: './menu.component.html',
    styleUrls: ['./menu.component.css'],
})
export class MenuComponent implements OnInit {
   constructor() { }
   
   ngOnInit() {
   }
}
```

### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component, OnInit } from '@angular/core';

@Component({
    selector: 'app-footer',
    templateUrl: './footer.component.html',
    styleUrls: ['./footer.component.css'],
    standalone: true // Generated - Change
})
export class FooterComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```
## 34. Step 29: Replace `@` with html ASCII code 
### frontend/todo/src/app/footer/footer.component.html

### BEFORE
```html
<span class="text-muted">All Rights Reserved 2018 @in28minutes</span>
```
### AFTER
```html
<span class="text-muted">All Rights Reserved 2024 &#64;in28minutes</span>
```

## 35. Step 30: Import routerLink to `menu.component.ts`
### frontend/todo/src/app/menu/menu.component.ts

```js
import { Component, OnInit } from '@angular/core';
import { RouterLink } from '@angular/router'; // Added

@Component({
    selector: 'app-footer',
    templateUrl: './footer.component.html',
    styleUrls: ['./footer.component.css'],
    standalone: true, // Generated - Change
    imports: [RouterLink] // Added
})
export class FooterComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

}
```

## 41. Step 34: Change - generated, No Update in app.module.ts(deleted in standalone)
### frontend/todo/src/logout/logout.component.ts

### BEFORE
```js
import { Component, OnInit} from '@angular/core';

@Component({
    selector: 'app-logout',
    templateUrl: './logout.component.html',
    styleUrls: ['./logout.component.css'],
})
export class LogoutComponent implements OnInit {
   constructor() { }

   ngOnInit() {
   }
}
```

### AFTER
> NOTE: In a standalone setup, the utilization of `@NgModule` and the `app.module.ts` file is not required, resulting in no updates being made.
```js
import { Component, OnInit } from '@angular/core';

@Component({
   selector: 'app-logout',
   templateUrl: './logout.component.html',
   styleUrls: ['./logout.component.css'],
   standalone: true // Generated - Change
})
export class LogoutComponent implements OnInit {
  
  constructor() { }

  ngOnInit() {
  }
}
```

