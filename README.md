# Semana de Ciências e Tecnologias - IFMS
## Tema: Angular CLI
## Autor : Rafael Viana

### Criação do Projeto
npm install  -g @angular/cli


### Bootrap 3.7

npm  install -s bootstrap

npm  install -s jquery

npm  install -s tether

      "styles": [
        "../node_modules/bootstrap/dist/css/bootstrap.min.css",
        "styles.css"
      ],
      "scripts": [
        "../node_modules/jquery/dist/jquery.js",
        "../node_modules/tether/dist/js/tether.js",
        "../node_modules/bootstrap/dist/js/bootstrap.js" ],
        
        
        
        

### Componentes
- () event binding: data flows out of
- [] property binding: data flows into

[Two-way-data-binding](https://angular.io/api)

                  import { Component } from '@angular/core';
                  import { User } from './shared/models/user';

                  @Component({
                    selector: 'my-app',
                    template: `
                      <header>
                        <nav class="navbar navbar-inverse">
                          <div class="navbar-header">
                            <a href="/" class="navbar-brand">My Angular 2 App!</a>
                          </div>
                        </nav>
                      </header>
                      <main>
                        <div class="row">
                          <div class="col-sm-4">
                            <div *ngIf="users">
                            <ul class="list-group users-list">
                              <li class="list-group-item"
                                *ngFor="let user of users"
                                (click)="selectUser(user)"
                                [class.active]="user === activeUser">
                                {{ user.name }} ({{ user.username }})
                              </li>
                            </ul>
                            </div>
                          </div>
                          <div class="col-sm-8">
                            <div class="jumbotron" *ngIf="activeUser">
                              <h2>{{ activeUser.name }} <small>{{ activeUser.username }}</small></h2>
                              <input class="form-control" [(ngModel)]="activeUser.name">
                            </div>
                            <div class="jumbotron" *ngIf="!activeUser">
                              <span class="glyphicon glyphicon-hand-left"></span>
                              <h2>Choose a User</h2>
                            </div>
                          </div>
                        </div>      
                      </main>
                      <footer class="text-center">
                        Copyright &copy; 2016
                      </footer>
                    `,
                    styles: [`
                      .users-list li   {
                        cursor: pointer;
                      }
                      .jumbotron .glyphicon {
                        font-size: 80px;
                      }
                    `]
                  })
                  export class AppComponent {
                    message: string = 'Hello!'; 
                    users: User[] = [
                      { id: 25, name: 'Chris', username: 'sevilayha' },
                      { id: 26, name: 'Nick', username: 'whatnicktweets' },
                      { id: 27, name: 'Holly', username: 'hollylawly' }
                    ];
                    activeUser: User;

                    selectUser(user) {
                      this.activeUser = user;
                      console.log(this.activeUser);
                    }
                  }
                  
[*ngIf](https://angular.io/api/common/NgIf)

            @Component({
                    selector: 'ng-if-simple',
                    template: `
                      <button (click)="show = !show">{{show ? 'hide' : 'show'}}</button>
                      show = {{show}}
                      <br>
                      <div *ngIf="show">Text to show</div>
                  `
                  })
                  class NgIfSimple {
                    show: boolean = true;
                  }
                  
 [ngStyle](https://angular.io/api/common/NgStyle)

                  <some-element [ngStyle]="{'font-style': styleExp}">...</some-element>

                  <some-element [ngStyle]="{'max-width.px': widthExp}">...</some-element>

                  <some-element [ngStyle]="objExp">...</some-element>                  
                  
         
 [Form](https://angular.io/api/common/NgStyle)
 
       //Configuração 
             import { NgForm } from '@angular/forms';
             import { BrowserModule } from '@angular/platform-browser';
             import { NgModule } from '@angular/core';
             import { AppComponent } from './app.component';
             import { FormsModule, ReactiveFormsModule }   from '@angular/forms';
             
              imports: [
                FormsModule,                               // <========== Add this line!
                ReactiveFormsModule,
                BrowserModule
              ],
              
             //Teste 1
                  //HTML
                        <input id="name" name="name" class="form-control"
                        required minlength="4" maxlength="10"
                        [(ngModel)]="nome" #name="ngModel" >

                        <div *ngIf="name.invalid && (name.dirty || name.touched)"
                              class="alert alert-danger">

                              <div *ngIf="name.errors.required">
                              Name is required.
                              </div>
                              <div *ngIf="name.errors.minlength">
                              Name must be at least 4 characters long.
                              </div>
                              <div *ngIf="name.errors.maxlength">
                                Name must be at least 4 characters long.
                              </div>
                        </div>
                  
                  //Component
                     nome;
                  
             //Teste 2
             
                  // HTML
                    <form #f="ngForm" (ngSubmit)="onSubmit(f)" novalidate>
                        <input name="first" ngModel required #first="ngModel">
                        <input name="last" ngModel>
                        <button>Submit</button>
                     </form>

                     <p>First name value: {{ first.value }}</p>
                     <p>First name valid: {{ first.valid }}</p>
                     <p>Form value: {{ f.value | json }}</p>
                     <p>Form valid: {{ f.valid }}</p>
                  
                  // Component
                        onSubmit(f: NgForm) {
                            console.log(f.value);  // { first: '', last: '' }
                            console.log(f.valid);  // false
                         }
                         
[Routing](https://angular.io/tutorial/toh-pt5)

        
        
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
                      RouterModule.forRoot(
                        appRoutes,
                        { enableTracing: true } // <-- debugging purposes only
                      )
                      // other imports here
                    ],
                    ...
                  })
        export class AppModule { }
