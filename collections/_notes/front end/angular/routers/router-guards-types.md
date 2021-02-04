---
layout: post
title: Types of Router Guards
permalink: /:collection/angular/routers/guards/type
---

* **CanActivate** - Checks if a user can visit a route.
  - **CanActivateChild** - Checks if a user can visit a route’s children.
* **CanDeactivate** - used to warn people if they are navigating away from a page where they have some unsaved changes.
* **Resolve** - Performs route data retrieval before route activation.
* **CanLoad** - Checks if a user can route to a module that lazy loaded.

```ts
import {CanActivate} from "@angular/router";

@Injectable
class AlwaysAuthGuard implements CanActivate {
  canActivate() {
    console.log("AlwaysAuthGuard");
    return true;
  }
}

@Injectable()
class OnlyLoggedInUsersGuard implements CanActivate {
  constructor(private userService: UserService) {};
  canActivate() {
    console.log("OnlyLoggedInUsers");
    if (this.userService.isLoggedIn()) {   return true;  } 
    else {
      window.alert("You don't have permission to view this page");
      return false;
    }
  }
}
```
```ts
@NgModule({
  ...
  providers: [    AlwaysAuthGuard  ]
})
```
```ts
const routes: Routes = [
  {path: '', redirectTo: 'home', pathMatch: 'full'},
  {path: 'find', redirectTo: 'search'},
  {path: 'home', component: HomeComponent},
  {path: 'search', component: SearchComponent},
  {
    path: 'artist/:artistId',
    component: ArtistComponent,
    canActivate: [OnlyLoggedInUsersGuard, AlwaysAuthGuard],
    children: [
      {path: '', redirectTo: 'tracks'},
      {path: 'tracks', component: ArtistTrackListComponent},
      {path: 'albums', component: ArtistAlbumListComponent},
    ]
  },
  {path: '**', component: HomeComponent}
];
```
