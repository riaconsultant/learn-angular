# Angular CLI

Hi All,

Today I am going to cover the Angular CLI useful command – I mostly cover all the command which is require to develop a application.

npm install -g @angular/cli@<Version_Number> — Install Angular NPM globally

npm uninstall -g @angular/cli@<Version_Number>

@<Version_Number> — is optional parameter.

npm cache clean — Clear the cache

npm cache verify — verify the npm cache is clear.

ng -v  – angular CLI version

ng new <APP_NAME> – create new Angular Application.

ng g m <Module_Name>- create Angular Module. m – Module

ng g m <Module_Name> –routing  — this will create routing module as well.

ng g c <Folder_Name>/<Component_Name>  — Create new Component <Folder_Name> is Optional.

— Flat true/false – Seperated folder or not.

–inline-template ( -it ) — Separated HTML template will not create.

–inline-style ( -is ) — Separated CSS or SCSS file will not create.

–spec ByDefault true can be fix false — will not create Unit test spec file.

–view-encapsulation( -ve ) – View Encapsulation Strategy

–change-detection ( -cd ) – can be set OnPush Strategy

–dry-run ( -d )

ng g s <Service_Name> — Generate the Service

ng g g <GUARD_Name> — Generate the Gurad class

ng g cl <Class_Name> — cl – Class  — Generate a Typescript class

ng g d <Directive_Name> — d – directive — Generate a Directive

ng g p <Pipe_Name> — p – Pipe  — Generate a Pipe

ng g i <Interface_Name> — i- Interface — Generate a Interface

ng g e <ENUM_Name> — e – Enum — Generate a Enum Class

ng serve — RUN Angular app default 4200 port

ng serve -o — will open the browser by default.

ng serve –port 8080 – Angular Application will run on the 8080 port

ng serve –live-reload – Reload when change occur

ng servev –ssl Using HTTPS

–proxy-config — pc —

ng serve -aot – Angular RUN same as in the production mode to avoid the surprise on the ng build

ng build –prod — Angular run on production build mode.

ng build -sm ( –sourcemap )

ng build –aot

ng build –watch

ng build –environment

ng build –target

ng build –dev

ng build –base-href (–bh)/<route_name>/  like /APP/

ng set defaults.styleExt scss – Angular CLI default stylesheet format is CSS. Can be change to SCSS file.

ng test –single-run

ng test –progress

ng test –colors

ng e2e –s ( Serve ) –ee ( element-explorer ) –c ( Config ) –sp ( specs ) –wu ( webdriver-update )




