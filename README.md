# angular-vscode-extension
VS Code extension that provides Angular language service via Typescript plugin.

## Disclaimer
* This is experimental feature, and it is meant to be proof-of-concept for the new
plugin [architecture](https://github.com/Microsoft/TypeScript/wiki/Writing-a-Language-Service-Plugin).
* This is different from the extension in the [Marketplace](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template).  The existing extension invokes its own Typescript server, which is slower and less efficient.

## Introduction
This extension is meant to be used in conjunction with the Angular Typescript plugin.
It tells VS Code to associate `.ng.html` files with the Angular plugin.
When external Angular templates are opened, VS Code would invoke the plugin to provide language service features.
Inline templates in Typescript files will continue to work as before.

## Installation
`code --install-extension <extension-vsix-path>`

## Packaging vsix
`yarn add vsce --dev`
`$(yarn bin)/vsce package`

## Location of `@angular/language-service`
Enabling plugin @angular/language-service from candidate paths:
* `/Applications/Visual Studio Code.app/Contents/Resources/app/extensions/node_modules/node_modules`
* `/Users/kyliau/.vscode/extensions/Angular.angular-language-service-0.0.1`

## Known Issues
1. Crash on startup with Typescript 2.6  
   Issue: https://github.com/Microsoft/TypeScript/issues/20321  
   Fix: https://github.com/kyliau/TypeScript/pull/1
2. Semantic errors (e.g. non-existent property) not shown on external template  
   Issue: https://github.com/Microsoft/TypeScript/issues/21280  
   Fix: https://github.com/kyliau/TypeScript/pull/2

## Questions

1. What if user specify the plugin in `tsconfig.json` via

```
{
  "compilerOptions" : {
    "plugins": [
      { "name" : "@angular/language-service" }
    ]
  }
}
```

Will this load the version of `@angular/language-service` installed by the user?
