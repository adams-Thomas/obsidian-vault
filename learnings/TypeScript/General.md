General Note for TypeScript Learnings and bits.

##### Types > Enums
Enums aren't really great, example:
```ts
enum UserRoles = [
	User, // 0
	Admin, // 1
	Staff // 2
];

 /**
 This will never get hit because the 0 of UserRoles.User is falsey
 **/
 if (UserRoles.User) {
	 console.log('Hello')
 }
```

Instead use Types, while this will get rid of the option of being able to iterate through the array. It will not give false falsey, etc.
Example:
```ts
const UserRoles = ['User', 'Admin', 'Staff'];
type UserRole = typeof UserRoles[number]
```
