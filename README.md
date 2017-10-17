# Semana de Ciências e Tecnologias - IFMS
## Tema: Angular CLI
## Autor : Rafael Viana


npm -install -s bootstrap

npm -install -s jquery

npm -install -s tether

      "styles": [
        "../node_modules/bootstrap/dist/css/bootstrap.min.css",
        "styles.css"
      ],
      "scripts": [
        "../node_modules/jquery/dist/jquery.js",
        "../node_modules/tether/dist/js/tether.js",
        "../node_modules/bootstrap/dist/js/bootstrap.js" ],
        
        
        
*NgIf https://angular.io/api/common/NgIf

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
