##The Basics

Most routing applications should add a <base> element to the index.html as the first child in the &lt;head&gt; tag to tell the router how to compose navigation URLs.

    src/index.html (base-href) <head> tag
    <base href="/">

###Router imports
It is not part of the Angular core. It is in its own library package, @angular/router. Import what you need from it as you would from any other Angular package.

    src/app/app.module.ts (import)
    import { RouterModule, Routes } from '@angular/router';

###Configuration
A routed Angular application has one, singleton instance of the Router service. When the browser's URL changes, that router looks for a corresponding Route from which it can determine the component to display.
A router has no routes until you configure it. The following example creates four route definitions, configures the router via the RouterModule.forRoot method, and adds the result to the AppModule's imports array.
    
    const appRoutes: Routes = [
      { path: 'crisis-center', component: CrisisListComponent },
      { path: 'hero/:id',      component: HeroDetailComponent },
      {
        path: 'heroes',
        component: HeroListComponent,
        data: { title: 'Heroes List' }
      },
      { path: '',
        redirectTo: '/heroes',
        pathMatch: 'full'
      },
      { path: '**', component: PageNotFoundComponent }
    ];

    @NgModule({
      imports: [
        RouterModule.forRoot(appRoutes)
        // other imports here
      ],
      ...
    })
    export class AppModule { }
    

###Router outlet
Given this configuration, when the browser URL for this application becomes /heroes, the router matches that URL to the route path /heroes and displays the HeroListComponent after a RouterOutlet that you've placed in the host view's HTML.

    <router-outlet></router-outlet>
    <!-- Routed views go here -->

###Router links
The URL could arrive directly from the browser address bar. But most of the time you navigate as a result of some user action such as the click of an anchor tag.

    template: `
      <h1>Angular Router</h1>
      <nav>
        <a routerLink="/crisis-center" routerLinkActive="active">Crisis Center</a>
        <a routerLink="/heroes" routerLinkActive="active">Heroes</a>
      </nav>
      <router-outlet></router-outlet>
    `
    
