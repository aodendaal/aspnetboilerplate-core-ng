# Creating Modal Dialogs
This article applies to ABP templates using __ngx-bootstrap__. You can find examples of modal dialogs in a clean template on _app/users_ and _app/tenants_ when creating a new user or tenant respectively.

### Calling component
```html
<!-- Trigger the modal with a button -->
<button data-toggle="modal" class="btn btn-primary pull-right" (click)="createUser()"><i class="fa fa-plus"></i> {{l('CreateNewUser')}}</button>
```

```javascript
import { Component, Injector, ViewChild } from '@angular/core';
...

import { CreateUserModalComponent } from './create-user-modal.component';

@Component({
    templateUrl: './users.component.html',
    animations: [appModuleAnimation()]
})
export class UsersComponent extends AppComponentBase {

    @ViewChild('createUserModal') createUserModal: CreateUserModalComponent;

    ...

    createUser(): void {
        this.createUserModal.show();
    }
}
```

### Modal component
```html
<div bsModal #createUserModal="bs-modal" class="modal fade" tabindex="-1" role="dialog" aria-labelledby="createUserModal" aria-hidden="true" [config]="{backdrop: 'static'}">
    <div class="modal-dialog">
        <div class="modal-content">
          ...
        </div>
    </div>
</div>
```

```javascript
import { Component, ViewChild, Injector, Output, EventEmitter, ElementRef } from '@angular/core';
import { ModalDirective } from 'ngx-bootstrap';
...
@Component({
    selector: 'createUserModal',
    templateUrl: './create-user-modal.component.html'
})
export class CreateUserModalComponent extends AppComponentBase {

    @ViewChild('createUserModal') modal: ModalDirective;

    @Output() modalSave: EventEmitter<any> = new EventEmitter<any>();

    active: boolean = false;
    saving: boolean = false;
    user: CreateUserInput = null;

    constructor(
        injector: Injector,
        private _userService: UserServiceProxy
    ) {
        super(injector);.
    }

    show(): void {
        this.active = true;
        this.modal.show();
        this.user = new CreateUserInput({ isActive: false });
    }

    save(): void {
        this.user.userName = this.user.emailAddress;
        this.saving = true;
        this._userService.createUser(this.user)
            .finally(() => { this.saving = false; })
            .subscribe(() => {
                this.notify.info(this.l('SavedSuccessfully'));
                this.close();
                this.modalSave.emit(null);
            });
    }

    close(): void {
        this.active = false;
        this.modal.hide();
    }
}
```


## See Also
* [ASP\.NET Boilerplate Tutorials](readme.md)
* [Project Architecture](projectarchitecture.md)
* [Frontend Built-in Functions](angularbuiltin.md)