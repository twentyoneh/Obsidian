Все Angular-приложения состоят из набора компонентов. Разные компоненты представляют собой независимые элементы с собственным поведением. Например, лента новостей и кнопка «Прочитать» — это два разных элемента подобного рода.
Любые компоненты можно подключить к основным либо дополнительным модулям, управляющим их работой. Основной модуль отвечает за контроль всего приложения, дополнительные отслеживают функционирование отдельных элементов.

Дополнительные модули назначены для выполнения конкретных узких задач, подчиняются основному, необходимы для оптимизации. Они отвечают за такие аспекты, как:

- навигация;
- анимация;
- взаимодействие с браузером;
- хранение компонентов.

```bash
ng new angular-16-crud --standalone=false
? Would you like to add Angular routing? Yes
? Which stylesheet format would you like to use? CSS
```

```bash
ng g s services/tutorial

ng g c components/add-tutorial
ng g c components/tutorial-details
ng g c components/tutorials-list

ng g class models/tutorial --type=model
```

### Set up App Module
На первом шаге подключим модуль форм
Open _app.module.ts_ and import `FormsModule`, `HttpClientModule`:
```js
import { FormsModule } from '@angular/forms';
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  declarations: [ ... ],
  imports: [
    ...
    FormsModule,
    HttpClientModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### Define Routes for Angular AppRoutingModule
На втором шаге пропишем конечные пути внутри которых будут расположены компоненты 
There are 3 main routes:  
– `/tutorials` for `tutorials-list` component  
– `/tutorials/:id` for `tutorial-details` component  
– `/add` for `add-tutorial` component

_app-routing.module.ts_

```js
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { TutorialsListComponent } from './components/tutorials-list/tutorials-list.component';
import { TutorialDetailsComponent } from './components/tutorial-details/tutorial-details.component';
import { AddTutorialComponent } from './components/add-tutorial/add-tutorial.component';

const routes: Routes = [
  { path: '', redirectTo: 'tutorials', pathMatch: 'full' },
  { path: 'tutorials', component: TutorialsListComponent },
  { path: 'tutorials/:id', component: TutorialDetailsComponent },
  { path: 'add', component: AddTutorialComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

### Define Model Class
Определяем как у нас будет выглядеть наша модель таблички 
Our main model class `Tutorial` will be exported in _tutorial.model.ts_ with 4 fields:

- `id`
- `title`
- `description`
- `published`

**models**/_tutorial.model.ts_

```js
export class Tutorial {
  id?: any;
  title?: string;
  description?: string;
  published?: boolean;
}
```

### Create Data Service
Определяем что будет происходить при переходе на ту или иную url
This service will use Angular `HttpClient` to send HTTP requests.  
You can see that its functions includes CRUD operations and finder method.

**services**/_tutorial.service.ts_

```js
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';
import { Tutorial } from '../models/tutorial.model';

const baseUrl = 'http://localhost:8080/api/tutorials';

@Injectable({
  providedIn: 'root'
})
export class TutorialService {

  constructor(private http: HttpClient) { }

  getAll(): Observable<Tutorial[]> {
    return this.http.get<Tutorial[]>(baseUrl);
  }

  get(id: any): Observable<Tutorial> {
    return this.http.get(`${baseUrl}/${id}`);
  }

  create(data: any): Observable<any> {
    return this.http.post(baseUrl, data);
  }

  update(id: any, data: any): Observable<any> {
    return this.http.put(`${baseUrl}/${id}`, data);
  }

  delete(id: any): Observable<any> {
    return this.http.delete(`${baseUrl}/${id}`);
  }

  deleteAll(): Observable<any> {
    return this.http.delete(baseUrl);
  }

  findByTitle(title: any): Observable<Tutorial[]> {
    return this.http.get<Tutorial[]>(`${baseUrl}?title=${title}`);
  }
}
```

## Import Bootstrap into Angular 16 Project
Библиотека для css для создания красивых сайтов 
Run the command: `npm install bootstrap.

Next, open **src**/_style.css_ and add following code:
```js
@import "~bootstrap/dist/css/bootstrap.css";
```

потом каждый компонент в .html файлах