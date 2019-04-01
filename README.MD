[![Dependency Status](https://dependencyci.com/github/mackelito/ng-zendesk-webwidget/badge)](https://dependencyci.com/github/mackelito/ng-zendesk-webwidget)
[![Maintainability](https://api.codeclimate.com/v1/badges/933c908a637cbd67013b/maintainability)](https://codeclimate.com/github/mackelito/ng-zendesk-webwidget/maintainability)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/mackelito/ng-zendesk-webwidget/issues)
[![codebeat badge](https://codebeat.co/badges/f912ceb9-f9e3-4ff4-9672-962d82c3a8be)](https://codebeat.co/projects/github-com-mackelito-ng-zendesk-webwidget-master)

# ng-zendesk-webwidget

Zendesk-Webwidget for Angular

* [Installation guide](#installation)
* [Usage](#usage)
* [API](#api)

## [](#installation)Installation


```bash
$ npm install ng-zendesk-webwidget --save
```
```bash
$ yarn add ng-zendesk-webwidget
```

## [](#usage)Usage

#### In app.module import `ZendeskWebwidgetModule`

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

import { ZendeskWebwidgetModule } from 'ng-zendesk-webwidget';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    ZendeskWebwidgetModule.forRoot()
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

##### Using a SharedModule

```ts
@NgModule({
    exports: [
        CommonModule,
        ZendeskWebwidgetModule
    ]
})
export class SharedModule { }
```

##### Configuration

```ts
import {NgModule} from '@angular/core';
import {BrowserModule} from '@angular/platform-browser';

import {ZendeskWebwidgetModule, ZendeskWebwidgetConfig} from 'ng-zendesk-webwidget';

import {AppComponent} from './app';

export class ZendeskConfig extends ZendeskWebwidgetConfig {
  accountUrl = 'yourdomain.zendesk.com';
  beforePageLoad(zE) {
    zE.setLocale('en');
    zE.hide();
  }
}

@NgModule({
    imports: [
        BrowserModule,
        HttpClientModule,
        ZendeskWebwidgetModule.forRoot(ZendeskConfig)
    ],
    bootstrap: [AppComponent]
})
export class AppModule { }
```

#### 2. Init the `ZendeskWebwidgetService` for your application:

```ts
import { ZendeskWebwidgetService } from 'ng-zendesk-webwidget';

@Component({
  selector: 'app',
  templateUrl: './app.html'
})
export class app {

  constructor(private _ZendeskWebwidgetService: ZendeskWebwidgetService) {
  }
}
```

#### 3. Example to usage:

```ts
  constructor(private _ZendeskWebwidgetService: ZendeskWebwidgetService) {
    _ZendeskWebwidgetService.identify({
     name: 'John Doe',
     email: 'John@doe.net'
    })
    _ZendeskWebwidgetService.show()
  }

  logout(){
    _ZendeskWebwidgetService.hide()
  }
}
```
## [](#api)API

### ZendeskWebwidgetService

#### Methods:
<!-- <table class="methods">
<style>
table.methods { padding: 0; margin: 0 0 -1px 0; }
.methods td { min-width: 200px; }
.methods td:last-child { width: 100%; }
</style>
  <tr>
    <td>`setLocale('en')`</td>
    <td>Set to change language</td>
  </tr>
</table>
<table class="methods">
    <tr>
        <td>`identify(userObj)`</td>
        <td>If your user is signed in, you can use this methods for to pass the details of that user to your Zendesk</td>
    </tr>
</table> -->

`setLocale('en')` Set to change language

`identify(userObj)` If your user is signed in, you can use this methods for to pass the details of that user to your Zendesk

`hide()`: The method completely hides all parts of the Widget from the page.

`show()`: The method displays the Widget on the host page in its starting 'button' state.

`activate(options)`: The method activates and opens the Widget in its starting state.

`setHelpCenterSuggestions(options)`: The method enhances the contextual help provided by the Web Widget.

`setSettings(settings)`: The method sets `window.zESettings`.

For more info, see: [ZendeskAPI](https://developer.zendesk.com/embeddables/docs/widget/api)

#### ZendeskWebwidgetConfig:

- `accountUrl`: Url of your domain (example.zendesk.com)
- `beforePageLoad`: Callback, executed after Zendesk loaded

## Issues

Please report bugs and issues [here](https://github.com/mackelito/ng-zendesk-webwidget/issues).

## License

MIT © [Markus Thiel](https://github.com/mackelito)
