# @ruanitto/ngx-local-storage

LocalStorageService for Angular with mostly the same API (and most of the code) from [angular-local-storage](https://github.com/grevory/angular-local-storage).

AoT compatible.

## NEW Feature added

* Addeded feature to encrypt/decrypt storage data

## Differences

* No events broadcast on $rootScope - LocalStorageService exposes observables for `errors$`,`removeItems$`, `setItems$` and `warning$` if you really need something to happen when something happens.
* The `bind` function doesn't work anymore (there is a stub so this can still be a drop-in, but it'll do nothing).

## Install

`npm install @ruanitto/ngx-local-storage`

## Usage

You can optionally configure the module:

```typescript
import { LocalStorageModule } from '@ruanitto/ngx-local-storage';

@NgModule({
    imports: [
        LocalStorageModule.forRoot({
            prefix: 'my-app',
            storageType: 'localStorage',
            encrypt: true,
            encryptKey: 'securekey'
        })
    ],
    declarations: [
        ..
    ],
    providers: [
        ..
    ],
    bootstrap: [AppComponent]
})
export class AppModule { }
```

Then you can use it in a component:

```typescript
import { LocalStorageService } from '@ruanitto/ngx-local-storage';

@Component({
    // ...
})
export class SomeComponent {
    constructor (
        private localStorageService: LocalStorageService
    ) {
        // YAY!
    }
}

```

### Configuration options

`import { ILocalStorageServiceConfig } from '@ruanitto/ngx-local-storage';` for type information about the configuration object.
