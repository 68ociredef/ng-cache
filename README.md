# ng-cache

A cache system for Angular applications.

## Getting started

Install ng-cache

```
npm install ng-cache
```

## Usage

```ts
import {ngCache} from 'ng-cache';
```

```ts
...
 //Http request
@ngCache()
public getUsers() {
    return this.http.get<User[]>('user')
}

//Value is stored in session storage if set a key
@ngCache('user')
public getUsers() {
    return this.http.get<User[]>('user')
}

//Dynamic composit key.
@ngCache('user{}') //key = user1 if id=1;
public getUserById(id: number) {
    return this.http.get<User>('user/'+ id)
}

//Sync method
@ngCache()
public method() {
    console.log("Call method")
    const length = 50000000;
    let item = 0;
    for(let index=0; index<length; index++) {
       item = item +1;
    }
    return item;
}


```

## Configuration

```ts
 //Local configuration.
 @ngCache(null, {expirationTime: 2*60000}) // in milliseconds

 //Global configuration.
 import {BzCacheModule} from 'ng-cache';

 @NgModule({
    .....
  BzCacheModule.forRoot(
    {
      expirationTime: 2*60000
    }
  )
   
   ......
```

## StackBlitz

[Link](https://stackblitz.com/edit/angular-ivy-mdzdrt?file=src%2Fapp%2Fapp.component.ts)

Please give to repo a **star** :star:.
