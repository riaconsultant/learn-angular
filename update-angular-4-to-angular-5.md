# Update Angular 4 to Angular 5
(https://flexmanu.files.wordpress.com/2018/02/screen-shot-2018-02-10-at-11-00-47-am.png)

Need to add npm module, which will compare the package.json and check the online version of latest release of the build.

NPM: npm install -g npm-check-updates (https://www.npmjs.com/package/npm-check-updates)

ncu -u to upgrade the application package.json after that need to remove the node_module folder and run the npm install.

This is very useful npm to upgrade any of the node projects. You can do similar thing manually but there a lot of problems might be faced due to the dependent version of other modules.

Major Changes of Angular5

1. AOT – is a major change that decreases the aot time.
2. HTTP module is there but introduce the HTTP client 
3. the zone is now a separate module.
4. Aotplugin is no more exist for webpack, Now AngularCompilePlugin is introduced.
5. PWA service-worker is introduced.
