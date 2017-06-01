[< Back to tutorial](README.md)

# Entity
More correctly called a Domain Entity.

ABP provides some interfaces for tracking when an entity was creation, last modified and deleted, as well as which user made the change.

You can use any of the interfaces but some do implement each other as shown in the tree view below:
* __IFullAudited__
  * __IAudited__
    * __ICreationAudited__ _(Adds CreatorUserId)_
      * __IHasCreationTime__ _(Adds CreationTime)_
    * __IModificationAudited__ _(LastModifierUserId)_
      * __IHasModificationTime__ _(Adds LastModificationTime)_
  * __IDeletionAudited__ _(Adds DeleterUserId and DeletionTime)_
    * __ISoftDelete__ _(Adds IsDeleted)_
* __IMustHaveTenant__
* __IMayHaveTenant__

[< Back to tutorial](README.md)