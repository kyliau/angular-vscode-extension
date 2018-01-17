# angular-vscode-extension
VSCode extension that provides Angular language service via Typescript plugin.

## Disclaimer
* This is experimental feature, and it is meant to be proof-of-concept for the new
plugin [architecture](https://github.com/Microsoft/TypeScript/wiki/Writing-a-Language-Service-Plugin).
* This is different from the extension in the [Marketplace](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template).  The existing extension invokes its own Typescript server, which is slower and less efficient.

## Introduction
This extension is meant to be used in conjunction with the Angular Typescript plugin.
It tells VSCode to associate `.ng.html` files with the Angular plugin, which would then invoke the plugin to enable language service features when external Angular templates are opened.
