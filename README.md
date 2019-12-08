# Angular
Angular 6 Basics

## module - consolidates different components
    declarations: components that are part of this module
    imports: list of dependency to other module
    exports: list of components you want to be accessed by other modules
    providers: list of services in your app

## component - binds the view, styling and services
    @Input - telling the app that this allows to pre-populate a value.
    
    :Angular life cycle hooks (https://angular.io/guide/lifecycle-hooks)
        ngOnChanges()
        ngOnInit()

        @Component - component
        @NgModule - module
        @Injectable - service
        

## Making REST calls with HttpClient
   #### 1. First is to import HttpClientModule into your root module.

        import { HttpClientModule } from '@angular/common/http';

   #### 2. Then you can now inject the httpClient service to the component.

        constructor(
            private http: HttpClient
        )
        
   #### 3. Then you can define the REST API call instantly inside ngOnInit function. This will return an Observable.
        (Note: You cannot asign the http request to a variable beacuse it's making an asynchronous call)

        let obs = this.http.get('https://api.github.com/users/foobearer');
        obs.subscribe((response) => console.log(response));


## Modular component structure using ng-content

 #### Reusing component and passing dynamic content

   #### Base structure:

        <div class="main-container">
            <div class="header">
                <h4 class="primary">/* Add another component */</h4>
                <span class="subheader-title"> /* Add subheading title here */ </span>
            </div>
            <div class="content">
                <div>
                /* Add modal content here */
                </div>
            </div>
            <div class="footer">
                <button class="btn-cancel">Cancel</button>
                <button class="btn-primary>Add</button>
            </div>
        </div>

   #### Multiple ng-content projections:

        <div class="main-container">
            <div class="header">
                <ng-content select="h4"></ng-content>
                <ng-content select="span"></ng-content>
            </div>
            <div class="content">
                <ng-content select="div">
                    /* Add modal content here */
                </ng-content>
            </div>
            <div class="footer">
                <button class="btn-cancel">Cancel</button>
                <button class="btn-primary>Add</button>
            </div>
        </div>

   #### Calling reusable component::

        <add-create-modal>
            <h4 class="primary"> /* Add another component */ </h4>
            <span class="subheader"> /* Add subheading title here */ </span>
            <div> /* Add modal content here */ </div>
        </add-create-modal>
        