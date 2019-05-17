# AngularCommunication1

![alt text](https://cdn-images-1.medium.com/max/800/1*0UMMKhV6_FdP0Rd7HjhYVw.png)

Imagine el caso de uso que tiene la barra lateral en su aplicación. La barra lateral está abierta o cerrada. Usted tiene el componente de la barra lateral y luego tiene un componente (o múltiples componentes) que puede abrirlo / cerrarlo o solicitar su estado. 

## Describiré tres formas de implementar este comportamiento.
### Pasando la referencia de un componente a otro
2. Comunicación a través del componente padre
3. Comunicación a través del Servicio
1. Pasando la referencia de un componente a otro.

Esta solución debe utilizarse cuando los componentes tienen dependencia entre ellos. Por ejemplo, desplegable, y desplegable para alternar. Por lo general, no pueden existir el uno sin el otro.
Crearemos el componente de barra lateral que tendrá el componente de barra lateral como entrada y al hacer clic en el botón de palanca abriremos / cerraremos el componente de barra lateral.
Aquí está el código relevante:

### app.component.html
app component

<app-side-bar-toggle [sideBar]="sideBar"></app-side-bar-toggle>
<app-side-bar #sideBar></app-side-bar>

### side-bar-toggle.component.ts
@Component({
  selector: 'app-side-bar-toggle',
  templateUrl: './side-bar-toggle.component.html',
  styleUrls: ['./side-bar-toggle.component.css']
})
export class SideBarToggleComponent {

  @Input() sideBar: SideBarComponent;

  @HostListener('click')
  click() {
    this.sideBar.toggle();
  }

}

### side-bar.component.ts
@Component({
  selector: 'app-side-bar-toggle',
  templateUrl: './side-bar-toggle.component.html',
  styleUrls: ['./side-bar-toggle.component.css']
})
export class SideBarToggleComponent {

  @Input() sideBar: SideBarComponent;

  @HostListener('click')
  click() {
    this.sideBar.toggle();
  }

}
Las importaciones se omiten en el código de TypeScript

Este proyecto se generó con [Angular CLI] (https://github.com/angular/angular-cli) versión 1.3.0.

## Development server

Ejecute `ng serve` para un servidor dev. Vaya a `http://localhost:4200/`. La aplicación se volverá a cargar automáticamente si cambia alguno de los archivos de origen.

## Code scaffolding

Ejecute `ng generar componente nombre-componente` para generar un nuevo componente. También puede usar`ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Ejecuta `ng build` para construir el proyecto. Los artefactos de compilación se almacenarán en el directorio `dist /`. Use la bandera `-prod` para una compilación de producción.

## Running unit tests

Ejecute `ng test` para ejecutar las pruebas unitarias a través de [Karma] (https://karma-runner.github.io).

## Running end-to-end tests

Ejecute `ng e2e` para ejecutar las pruebas de extremo a extremo a través de [Protractor] (http://www.protractortest.org/).
Antes de ejecutar las pruebas, asegúrese de que está sirviendo la aplicación a través de `ng serve`.

## Further help

Para obtener más ayuda sobre Angular CLI, use `ng help` o visite el [Angular CLI README] (https://github.com/angular/angular-cli/blob/master/README.md).
