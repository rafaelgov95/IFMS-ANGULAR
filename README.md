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
