# Laravel Style Guide

## Naming

### **Database Table**

DB tables should be descriptive in plural form, with underscores to separate words (snake_case) and lower case

- Good Examples:

  - posts
  - project_tasks
  - uploaded_images

- Bad example
  - all_posts ( good but the "all" gives an ambiguous meaning)
  - Posts ( not in lowercase)
  - post ( not in plural form)
  - blogPosts ( not in snake_case and lowercase)

#### Pivot tables

Pivot tables should be all lower case, with each model in alphabetical order, noun formation descriptive on the relationship and separated by an underscore (snake_case).

- Good examples:

  - post_user
  - task_user

- Bad examples:
- users_posts ( not descriptive of the relationship)
- UsersPosts ( not in snake case)
- users_abc ( abc is not a model entity, not in alphabetical order)

#### Table columns names

Table column names should be in lower case, and snake_case (underscores between words). You shouldn't reference the table name.

- For example: post_body, id, created_at.
- Bad examples: blog_post_created_at, forum_thread_title, threadTitle.

#### Primary Key

This should normally be id.

#### Foreign Keys

Foreign keys should be the model name (singular), with '\_id' appended to it (assuming the PK in the other table is 'id').

- For example: comment_id, user_id.

#### Variables

Normal variables should typically be in camelCase, with the first character lower case.

For example: $users = ..., $bannedUsers = ....
Bad examples: $all_banned_users = ..., $Users=....

If the variable contains an array or collection of multiple items then the variable name should be in plural. Otherwise, it should be in singular form.

For example: `$users = User::all();` (as this will be a collection of multiple User objects), but \$user = User::first() (as this is just one object)

### **Naming Conventions for models**

#### Naming Models in Laravel

A model should be in singular, no spacing between words, and capitalised.

- For example: User (\App\User or \App\Models\User, etc), ForumThread, Comment.
- Bad examples: Users, ForumPosts, blogpost, blog_post, Blog_posts.

Generally, your models should be able to automatically work out what database table it should use from the following laravel method:

        /**
         * Get the table associated with the model.
         *
         * @return string
         */
        public function getTable()
        {
            if (! isset($this->table)) {
                return str_replace(
                    '\\', '', Str::snake(Str::plural(class_basename($this)))
                );
            }

            return $this->table;
        }

But of course you can just set `$this->table in your model`.

Creating models and migrations at the same time by running `php artisan make:model -m ForumPost` is **recommended**. This will auto-generate the migration file (in this case, for a DB table name of `forum_posts`).

#### Model properties

These should be lower case, snake_case. Generally they should also follow the same conventions as the table column names.

- For example: $this->updated_at, $this->title.
- Bad examples: $this->UpdatedAt, $this->blogTitle.

#### Model Methods

Methods in your models in Laravel projects, like all methods in your Laravel projects, should be camelCase.

- For example: public function get(), public function getAll().
- Bad examples: public function GetPosts(), public function get_posts().

### **Relationships**

#### hasOne or belongsTo relationship (one to many)

These should be singular form and follow the same naming conventions of normal model methods (camelCase)

- For example: public function postAuthor(), public function phone().

#### hasMany, belongsToMany, hasManyThrough (one to many)

These should be the same as the one to many naming conventions, however, its should be in plural.

- For example: public function comments(), public function roles().

#### Polymorphic relationships

These can be a bit awkward to get the naming correct.

Ideally, you want to be able to have a method such as this:

    public function category()
    {
        return $this->morphMany('App\Category', 'categoryable');
    }

And Laravel will by default assume that there is a categoryable_id and categoryable_type.

But you can use the other optional parameters for `morphMany ( public function morphMany($related, $name, $type = null, $id = null, \$localKey = null))` to change the defaults.

## Controllers

### Naming Controller

Controllers should be in singular form, Uppercase First Letter of every word (PascalCase), no spacing between words, and ends with "Controller".

- Good Examples:

  - BlogController,
  - AuthController
  - UserController

- Bad examples:
  - **UsersController** (because it is in plural),
  - **Users** (because it is missing the Controller suffix).

### Naming Methods in controllers

These should follow the same rules as model methods. I.e. camelCase (first character lowercase).

In addition, for normal CRUD operations, they should use one of the following method names.

    Verb        URI                     Method Name     Route Name
    GET         /photos                 index()         photos.index
    GET         /photos/create          create()        photos.create
    POST        /photos                 store()         photos.store
    GET         /photos/{photo}         show()          photos.show
    GET         /photos/{photo}/edit    edit()          photos.edit
    PUT/PATCH   /photos/{photo}         update()        photos.update
    DELETE      /photos/{photo}         destroy()       photos.destroy

## Traits

Traits should be be singular adjective words.

- For example: Notifiable, Dispatchable

## Blade view files

Blade files should be in snake_case.

- For example: all.blade.php, all_posts.blade.php
