# FirstAngularApp-

//app.component.html
//creating Nav Bar in app html

<header>
  <div class="container">
    <a href="#" class="logo">CoolApp</a>
    <nav>
      <ul>
        <li><a href="a" routerLink="/">Home</a></li>
        <li><a href="a" routerLink="/list">Brewies</a></li>
        <li><a href="a" routerLink="/conract">Contact</a></li>
      </ul>
    </nav>

  </div>
</header>

//home.component.html
//Creating 3 div 

<h1>Welcome!</h1>

<div class="play-container">
  <p>You've clicked <span (click)="countClick()">this</span> {{ clickCounter }} times.</p>
                        // on the case of click this counterclick function will be called
                        //and increment clickCounter 
</div>


<div class="play-container">
  <p>
     <input type="text" [(ngModel)]="name"> //name is property class HomeComponent 
     <br>
     <strong>You said: </strong> {{ name }}
  </p>
</div>

<div class="play-container" [ngClass]="setClasses()">   //setClasses is method in class HomeComponent
  <ng-template [ngIf]="clickCounter > 4" [ngIfElse]="none">  //if clickCounter > 4 else none 
    <p>The click counter <strong>IS GREATER</strong> than 4.</p>
  </ng-template>

  <ng-template #none>
    <p>The click counter is <strong>not greater</strong> than 4</p>
  </ng-template>
</div>


//Home-Componenet-TS

import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.scss']
})
export class HomeComponent implements OnInit {

  clickCounter: number = 0;
  name: string = "HHHHH";


  constructor() { }

  ngOnInit() {
  }

  countClick() {
    this.clickCounter += 1;
  }

  setClasses() {

    let myClasses = {
      active: this.clickCounter > 4,
      notactive: this.clickCounter <= 4,
    };

    return myClasses;
  }

}
