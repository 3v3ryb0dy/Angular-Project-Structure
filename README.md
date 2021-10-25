# Recommended Angular Project Structure

```
|-- app
     |-- modules
        |-- home
           |-- [+] components
           |-- [+] pages
           |-- home-routing.module.ts
           |-- home.module.ts
     |
     |-- core
        |-- [+] authentication
        |-- [+] footer
        |-- [+] guards
        |-- [+] http
        |-- [+] interceptors
        |-- [+] mocks
        |-- [+] services
        |-- [+] header
        |-- core.module.ts
        |-- ensureModuleLoadedOnceGuard.ts
        |-- logger.service.ts
     |
     |-- shared
        |-- [+] components
        |-- [+] directives
        |-- [+] pipes
        |-- [+] models
	|-- [+] state
     |
     |-- [+] configs
|-- assets
     |-- scss
        |-- [+] partials
        |-- _base.scss
        |-- styles.scss
```

## Modules

Modules reside in their own space with designated folders for pages- and components. It’s perfect for scaling and component- and page logic are separated.

### Core Module

The `CoreModule` takes on the role of the root `AppModule`, but is not the module which gets bootstrapped by Angular at run-time. The `CoreModule` should contain singleton services, universal components and other features where there’s only once instance per application. To prevent re-importing the core module elsewhere, you should also add a guard for it in the core module’s constructor.

### Shared Module

The `SharedModule` is where any shared components, pipes/filters and services should go. The `SharedModule` can be imported in any other module when those items will be re-used. The shared module shouldn’t have any dependency to the rest of the application and should therefore not rely on any other module.

## Configs

The config folder contains app settings and other predefined values.

## Assets

The global styles for the project are placed in a `scss` folder under `assets`.\
The `scss` folder does only contain one folder — partials. Partial-files can be imported by other scss files. E.g., `styles.scss` imports all the partials to apply their styling.


Inspired by: https://itnext.io/choosing-a-highly-scalable-folder-structure-in-angular-d987de65ec7 
