# workshop-strapi

This workshop is an introduction to the `Strapi` tool for an easy backend creation.

This workshop was made by:
* william.bulin@epitech.eu
* lucas.claisse@epitech.eu

---

## Requirements

Docker (see Startup part)

[Postman](https://www.postman.com/)

---

## Startup

For this project, you'll need to clone this repository

```bash
git clone git@github.com:LucasClaisse/workshop-strapi.git
```

and you'll need `docker` and `docker-compose` installed on your computer

```bash
# Fedora 26
sudo dnf install docker docker-compose
```

You'll then need to start the docker service

```bash
sudo systemctl start docker.service
```

You can now launch the strapi application by running the following command from within the previously downloaded repository

```bash
docker-compose up --build
```

---

## Documentation

You'll find the  `strapi` documentation [here](https://strapi.io/documentation/3.0.0-beta.x/getting-started/introduction.html).


---

## Exercices

`First thing, do not use personal data on this exercices (personal password or emails) since the app in not secured to make it easier, the data send are not safe.`

Before starting, you'll need an admin account, you can create one by going on the url [http://localhost/](http://localhost/) when the application is running

***For exercice I and II, postman already created everything you need, it is just for you to understand how to communicate with your Application***

### Exercice I

You should already be abble to create an account, try to create one with `Postman`

### Exercice II

Now that you have create an account, try to loggin to that account with `Postman`

### Exercice III

Now that you have the bases, we will try to actually start using strapi.
For that, get to the url: http://localhost/admin/ and create an admin account if not already done.

Now, you'll create a new `Content Type`, it's called a table in SQL.
Your table will be called `Profile` and will contains the following rows

* age: Number, it's an integer required field with a minimum value of 0 (see the advanced settings in strapi).
* date_of_birth: Date, it's a date not required field.
* major: boolean, it's a private and required field.

When your `Content Type` is done, do not forget to save your changes!

Once it's done, you should see a new `Content Type` on the left side of your admin page, create a new profile and put fake informations in it.

### Exercice IV

Now, you have create your first `Content Type`, but it is not actualy accessible with the api, you need to specify the permissions on this `Content Type`, take a look at the `Roles and Permissions` tab on the strapi admin page. Every user should be able to perform every requests on the `Profile` Content Type, change the permissions as requested and try to retrieve the number of profiles you have created with `Postman`.

To confirm that it's working, create a new profile and retry the same request.

### Exercice V

You should now be able to retrieve a list of all profiles, try to find this list, it should look liike this

```json
[
    {
        "id": 1,
        "age": 14,
        "date_of_birth": "2020-02-11",
        "created_at": "2020-02-04T16:09:41.061Z",
        "updated_at": "2020-02-04T16:09:41.061Z"
    },
    {
        "id": 2,
        "age": 21,
        "date_of_birth": "2020-02-10",
        "created_at": "2020-02-04T16:14:22.896Z",
        "updated_at": "2020-02-04T16:14:22.896Z"
    }
]
```

### Exercice VI

Now that you know how `Content Types` work, you can now try to link a profile to a user, to link 2 tables, you use what is called a `Relation`.

So, you can go back to your `Content Type Builder` and add a field to the `Profile` Content Type. it should be as followed:

* 1 user can have 1 Profile and 1 Profile can have 1 user (yes, it's not the same)
* the field name is `user` from the `Profile` Content Type
* the field name is `profile` from the `User` Content Type

***Don't forget to save***

Now you should be able to link one of your previously created profile to the account you created in `Exercice I`