# Ng2-Restangular

Ng2-Restangular is an Angular 2 service that simplifies common GET, POST, DELETE, and UPDATE requests with a minimum of client code.
It's a perfect fit for any WebApp that consumes data from a RESTful API.


# Starter Guide

## Quick Configuration (For Lazy Readers)
This is all you need to start using all the basic Restangular features.

````javascript
import { NgModule } from '@angular/core';
import { AppComponent } from './app.component';
import { RestangularModule, Restangular } from 'ng2-restangular';

// Function for settting the default restangular configuration
export function RestangularConfigFactory (RestangularProvider) {
  RestangularProvider.setBaseUrl('http://api.restng2.local/v1');
  RestangularProvider.setDefaultHeaders({'Authorization': 'Bearer UDXPx-Xko0w4BRKajozCVy20X11MRZs1'});
}

// AppModule is the main entry point into Angular2 bootstraping process
@NgModule({
  bootstrap: [ AppComponent ],
  declarations: [
    AppComponent,
  ],
  imports: [
    // Importing RestangularModule and making default configs for restanglar
    RestangularModule.forRoot(RestangularConfigFactory),
  ]
})
export class AppModule {
}

// later in code ...

@Component({
  ...
})
export class OtherComponent {
  constructor(private restangular: Restangular) {
  }

  ngOnInit() {
    // GET http://api.test.local/v1/users/2/accounts
    this.restangular.one('users', 2).all('accounts').getList();
  }
````
