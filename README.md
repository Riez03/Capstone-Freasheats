<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## API Documentation
Base URL: https://96a6-180-254-59-239.ngrok-free.app

## Login

Endpoint : POST https://96a6-180-254-59-239.ngrok-free.app/api/login

Request Body :

```json
{
    "email" : "admin@gmail.com",
    "password" : "admin123@gmail.com"
}
```

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Authenticated"
    },
    "data": {
        "access_token": "1|T0DisBRKoaxKudyTk9DEHlMx4XHsG7BN66TwlvP1e24ec6d4",
        "token_type": "Bearer",
        "user": {
            "id": 1,
            "name": "admin",
            "email": "admin@gmail.com",
            "email_verified_at": null,
            "two_factor_confirmed_at": null,
            "profile_photo_path": null,
            "created_at": 1700883242,
            "updated_at": 1700883242,
            "address": "secret",
            "phone_number": "012345",
            "city": "secret",
            "roles": "ADMIN",
            "profile_photo_url": "https://ui-avatars.com/api/?name=a&color=7F9CF5&background=EBF4FF"
        }
    }
}
```
Response Body (failed) :

```json
{
    "meta": {
        "code": 500,
        "status": "error",
        "message": "Authentication Failed"
    },
    "data": {
        "message": "Unauthorization"
    }
}
```

## Register

Endpoint : POST https://96a6-180-254-59-239.ngrok-free.app/api/register

Request Body :

```json
{
    "name" : "budi",
    "email" : "budi@gmail.com",
    "password" : "12345678",
    "password_confirmation" : "12345678",
    "address" : "Bantul",
    "city"  : "Bandung",
    "phone_number" : "08128373728"
}
```

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": null
    },
    "data": {
        "access_token": "3|kuNEQ0KBUltRHDXddmbE3eXGxRyyP4WlxzSUvvyU92730905",
        "token_type": "Bearer",
        "user": {
            "id": 4,
            "name": "test2",
            "email": "test2@gmail.com",
            "email_verified_at": null,
            "two_factor_confirmed_at": null,
            "profile_photo_path": null,
            "created_at": 1700928994,
            "updated_at": 1700928994,
            "address": "Jalan Jenderal Sudirman",
            "phone_number": null,
            "city": "Bandung",
            "roles": "USER",
            "profile_photo_url": "https://ui-avatars.com/api/?name=t&color=7F9CF5&background=EBF4FF"
        }
    }
}
```

Response Body (failed) :

```json
{
    "meta": {
        "code": 500,
        "status": "error",
        "message": "Authentication failed"
    },
    "data": {
        "message": "Something get wrong",
        "error": {
            "validator": {
                "customMessages": [],
                "fallbackMessages": [],
                "customAttributes": [],
                "customValues": [],
                "excludeUnvalidatedArrayKeys": true,
                "extensions": [],
                "replacers": []
            },
            "response": null,
            "status": 422,
            "errorBag": "default",
            "redirectTo": null
        }
    }
}
```

## Upload Profile

Endpoint : POST https://96a6-180-254-59-239.ngrok-free.app/api/user/photo
Authorization Type Bearer Token : "USER_TOKEN" 

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": null
    },
    "data": [
        "assets/user/ibAZGgxqaU3GfZKm6WO6KGQsVpYrraHxFRwjEOkD.png",
        "Success upload file"
    ]
}
```

Response Body (failed) :

```json
{
    "meta": {
        "code": 400,
        "status": "error",
        "message": "Update photo failed"
    },
    "data": {
        "error": {
            "file": [
                "The file field is required."
            ]
        }
    }
}
```

## Checkout

Endpoint : POST https://96a6-180-254-59-239.ngrok-free.app/api/checkout

Authorization Type Bearer Token : "USER_TOKEN" 

Request Body :

```json
{
  "ingredients_id" : "1",
  "user_id"        : "2",
  "quantity"       : "2",
  "total"          : "10000",
  "status"         : "On_Delivered"
}
```

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Transaksi berhasil"
    },
    "data": {
        "id": 18,
        "user_id": 2,
        "ingredients_id": 1,
        "quantity": 1,
        "total": "999000",
        "status": "CANCELLED",
        "payment_url": "https://app.sandbox.midtrans.com/snap/v3/redirection/b1b980c1-51da-41c8-b9dc-03bd8df7b9dc",
        "deleted_at": null,
        "created_at": 1700931534,
        "updated_at": 1700931537,
        "ingredients": [
            {
                "id": 1,
                "name": "Apel",
                "description": "Apel bervitamin",
                "price": 10000,
                "rate": 2.5,
                "types": "Buah",
                "stock": 20,
                "picture_path": "assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png",
                "deleted_at": null,
                "created_at": 1700911163,
                "updated_at": 1700911163,
                "picture_path_url": "http://96a6-180-254-59-239.ngrok-free.app/storage/assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png"
            }
        ],
        "user": {
            "id": 2,
            "name": "test1",
            "email": "test1@gmail.com",
            "email_verified_at": null,
            "two_factor_confirmed_at": null,
            "profile_photo_path": "assets/user/7EMHqkJFpfzatUXsCikR3CJGa1W2ljpmynZPmlA2.png",
            "created_at": 1700919078,
            "updated_at": 1700919078,
            "address": "bantul",
            "phone_number": null,
            "city": "bantul",
            "roles": "USER",
            "profile_photo_url": "https://96a6-180-254-59-239.ngrok-free.app/storage/assets/user/7EMHqkJFpfzatUXsCikR3CJGa1W2ljpmynZPmlA2.png"
        }
    }
}
```

Response Body (failed) :

```json
{
    "message": "Unauthenticated."
}
```

## GET User

Endpoint : GET https://96a6-180-254-59-239.ngrok-free.app/api/user
Authorization Type Bearer Token : "USER_TOKEN" 

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Data profile berhasil di ambil"
    },
    "data": {
        "id": 1,
        "name": "admin",
        "email": "admin@gmail.com",
        "email_verified_at": null,
        "two_factor_confirmed_at": null,
        "profile_photo_path": "assets/user/ibAZGgxqaU3GfZKm6WO6KGQsVpYrraHxFRwjEOkD.png",
        "created_at": 1700883242,
        "updated_at": 1700929699,
        "address": "secret",
        "phone_number": "012345",
        "city": "secret",
        "roles": "ADMIN",
        "profile_photo_url": "https://96a6-180-254-59-239.ngrok-free.app/storage/assets/user/ibAZGgxqaU3GfZKm6WO6KGQsVpYrraHxFRwjEOkD.png"
    }
}
```

Response Body (failed) :

```json
{
    "message": "Unauthenticated."
}
```

## GET Ingredients

Endpoint : GET https://96a6-180-254-59-239.ngrok-free.app/api/ingredients

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Data list produk berhasil diambil"
    },
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": 1,
                "name": "Apel",
                "description": "Apel bervitamin",
                "price": 10000,
                "rate": 2.5,
                "types": "Buah",
                "stock": 20,
                "picture_path": "assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png",
                "deleted_at": null,
                "created_at": 1700911163,
                "updated_at": 1700911163,
                "picture_path_url": "http://96a6-180-254-59-239.ngrok-free.app/storage/assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png"
            },
            {
                "id": 2,
                "name": "durian",
                "description": "rere",
                "price": 12345,
                "rate": 2,
                "types": "Buah",
                "stock": 155,
                "picture_path": "assets/ingredients/Ez1vdTtO1mqFexIQsjHZLx60tuJUhoI4mR3SqC47.png",
                "deleted_at": null,
                "created_at": 1700911318,
                "updated_at": 1700919283,
                "picture_path_url": "http://96a6-180-254-59-239.ngrok-free.app/storage/assets/ingredients/Ez1vdTtO1mqFexIQsjHZLx60tuJUhoI4mR3SqC47.png"
            },
            {
                "id": 4,
                "name": "apel",
                "description": "adasd",
                "price": 12331,
                "rate": 2,
                "types": "Buah",
                "stock": 23,
                "picture_path": "assets/ingredients/V45fe6mDAmnspzNwzrOcxNEN8WQZTIkk4Blk2YEt.png",
                "deleted_at": null,
                "created_at": 1700916535,
                "updated_at": 1700916535,
                "picture_path_url": "http://96a6-180-254-59-239.ngrok-free.app/storage/assets/ingredients/V45fe6mDAmnspzNwzrOcxNEN8WQZTIkk4Blk2YEt.png"
            }
        ],
        "first_page_url": "http://96a6-180-254-59-239.ngrok-free.app/api/ingredients?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://96a6-180-254-59-239.ngrok-free.app/api/ingredients?page=1",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://96a6-180-254-59-239.ngrok-free.app/api/ingredients?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": null,
        "path": "http://96a6-180-254-59-239.ngrok-free.app/api/ingredients",
        "per_page": 15,
        "prev_page_url": null,
        "to": 3,
        "total": 3
    }
}
```

## GET Transaction

Endpoint : GET https://96a6-180-254-59-239.ngrok-free.app/api/transaction
Authorization Type Bearer Token : "USER_TOKEN" 

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Data list transaksi berhasil diambil"
    },
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": 1,
                "user_id": 1,
                "ingredients_id": 1,
                "quantity": 1,
                "total": "1",
                "status": "CANCELLED",
                "payment_url": "https://github.com/Midtrans/midtrans-php",
                "deleted_at": null,
                "created_at": 1699395904,
                "updated_at": 1700919742,
                "ingredients": [
                    {
                        "id": 1,
                        "name": "Apel",
                        "description": "Apel bervitamin",
                        "price": 10000,
                        "rate": 2.5,
                        "types": "Buah",
                        "stock": 20,
                        "picture_path": "assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png",
                        "deleted_at": null,
                        "created_at": 1700911163,
                        "updated_at": 1700911163,
                        "picture_path_url": "http://96a6-180-254-59-239.ngrok-free.app/storage/assets/ingredients/AC4fQlQBXL8m5jisYSRKtIXVlX4lGsd6a7llrw4l.png"
                    }
                ],
                "user": {
                    "id": 1,
                    "name": "admin",
                    "email": "admin@gmail.com",
                    "email_verified_at": null,
                    "two_factor_confirmed_at": null,
                    "profile_photo_path": "assets/user/ibAZGgxqaU3GfZKm6WO6KGQsVpYrraHxFRwjEOkD.png",
                    "created_at": 1700883242,
                    "updated_at": 1700929699,
                    "address": "secret",
                    "phone_number": "012345",
                    "city": "secret",
                    "roles": "ADMIN",
                    "profile_photo_url": "https://96a6-180-254-59-239.ngrok-free.app/storage/assets/user/ibAZGgxqaU3GfZKm6WO6KGQsVpYrraHxFRwjEOkD.png"
                }
            }
        ],
        "first_page_url": "http://96a6-180-254-59-239.ngrok-free.app/api/transaction?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "http://96a6-180-254-59-239.ngrok-free.app/api/transaction?page=1",
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "http://96a6-180-254-59-239.ngrok-free.app/api/transaction?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "next_page_url": null,
        "path": "http://96a6-180-254-59-239.ngrok-free.app/api/transaction",
        "per_page": 15,
        "prev_page_url": null,
        "to": 1,
        "total": 1
    }
}
```

Response Body (failed) :

```json
{
    "message": "Unauthenticated."
}
```

## Logout

Endpoint : POST https://96a6-180-254-59-239.ngrok-free.app/api/logout
Authorization Type Bearer Token : "USER_TOKEN" 

Response Body (succes) :

```json
{
    "meta": {
        "code": 200,
        "status": "success",
        "message": "Token Revoked"
    },
    "data": {
        "success": true
    }
}
```

Response Body (failed) :

```json
{
    "message": "Unauthenticated."
}
```

## Contributing

-
-
-

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
