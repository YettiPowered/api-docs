# Users API

> All users are equal. Just some are more equal than others.

## Available methods

### User methods

* `GET /users.ws` lists user types.
* `GET /users/[type-id].ws` lists users of the given type.
* `GET /users/[type-id]/[user-id].ws` fetches the user with the given ID.
* `POST /users/[type-id].ws` creates a user of the given type.
* `PUT /users/[type-id]/[user-id].ws` updates the user with the given ID.
* `DELETE /users/[type-id]/[user-id].ws` deletes the user with the given ID.
* `GET /templates/user/[type-id].ws` fetch a blank template for a user of the given type.

### User address methods

* `GET /users/[type-id]/[user-id]/addresses.ws` list addresses for a user.
* `POST /users/[type-id]/[user-id]/addresses.ws` creates a new address for a user.
* `GET /users/[type-id]/[user-id]/addresses/[address-id].ws` fetch an individual address for a user.
* `PUT /users/[type-id]/[user-id]/addresses/[address-id].ws` updates the address with the given ID.
* `DELETE /users/[type-id]/[user-id]/addresses/[address-id].ws` deletes the address with the given ID.

## Details

User operations are almost identical to operations on item resources. We'll document particular differences here, but for the most part please refer to [items](items.md).
