# Read URL query parameters
```typescript
import { Router, ActivatedRoute, Params } from '@angular/router';
```

Inject ```private route: ActivatedRoute```

Use ```this.route.queryParams``` which returns ```Observable<Params>```. ```Params``` is a key-string array.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Creating modal dialogs](modals.md)
* [Built-in Functions](angularbuiltin.md)