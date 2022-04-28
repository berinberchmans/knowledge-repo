---
description: How to create angular libraries and upload them to npm.
---

# Creating Angular Libraries

### Creating your project

First, you need to initialize your project. You can set a prefix to the project using the `--prefix` command and entering the prefix after it.

```
ng new lib-demo --prefix ld
```

### Generating Library

Next we need to generate our library.  Again, --prefix is used to give our library a prefix.

```
ng generate library myLibrary --prefix abc 
```

### Building Library

Once we generate our library, and write our code inside the library component, we need to build the library so as to use it in our project. This build is not in production form yet.&#x20;

```
ng build myLibrary 
```

### &#x20;Using the Library

The files we build here can be used directly in the project we are using to make the library. But first we need to import it into our project. Open the _`src/app/app.component.ts`  _  file and import the library into the file.

```
import { MyLibraryModule } from 'myLibrary';
@NgModule({
    imports:[MyLibraryModule]
})
```

### Publishing the library

Once we are happy with out library, we can publish it to _npm._ You ween need to have the npm cli installed and log into your account. Then run `ng build` with the `--prod` command. The package will be found under the _`dist`_ folder. Go into the package folder and run `npm publish`.

```
ng build myLibrary --prod
cd dist/myLibrary 
npm publish
```

### Editing the library while project is running

There will come situations where we will have to debug or edit our library. It is difficult to generate the library each time. Use `--watch` command when building to "watch" the library files for any change. If we are running our project using `serve` as well, it will reload anytime we make a change in the library files.

```
ng build myLibrary --watch
```
