# Localize

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 17.0.10.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


# description

this project is for learning localization and how to add multiple language support in angular

# steps

after setting up new project using ng new project name 

1. ng add @angular/localize
2. under assets create i18n folder and keep your json files for different language there
3.  in angular.json under localize add i18n option and under that add sourcelocale(default language) and locales(map json files in i18n folder)
4. run npm i @ngx-translate/core and npm i @ngx-translate/http-loader
5. add this code in app module
  export function httpLoaderFactory(http:HttpClient){
   return new TranslateHttpLoader(http,'./assets/i18n/','.json')
}

@NgModule({
  declarations: [],
  imports: [
    CommonModule,
    BrowserModule, 
    AppRoutingModule,
    HttpClientModule,
    TranslateModule.forRoot({
      loader:{
        provide:TranslateLoader,
        useFactory:httpLoaderFactory,
        deps:[HttpClient]
      }
    })
  ],
  bootstrap:[AppComponent]
})
export class AppModule { }