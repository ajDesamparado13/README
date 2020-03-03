# Coding Documentation

## Why do you need code documentation?

There are several reasons why code documentation is crucial for any project.

- It is good for knowledge transfer. Not all code is equally obvious. There might be some complex algorithms or custom workarounds that are not clear enough for other developers.
- It helps to troubleshoot production issues. If there are any problems with the product after it’s released, having proper documentation can speed up the resolution time. Finding out product details and architecture specifics is a time-consuming task, which results in the waste of money.
- It may help better management of any additional integrations and product add-ons. Product documentation describes dependencies between system modules and third-party tools. Thus, it may be needed for integration purposes.

**All in all, having application properly documented will make the development and maintenance efforts more efficient and will save time and money in the long run.**

## What does good documentation consist of?

Having no documents at all is as bad as having excessive or inappropriate documentation.
Here are some basic rules for creating useful and, most importantly, usable code documentation.

1. Keep it simple and concise. Follow the DRY (Don’t Repeat Yourself) principle. It is not necessary to comment on every single line of code, use comments to explain something that really needs explaining and is not self-evident.
2. Keep it up to date at all times. It’s best to document the code step by step, as it is written, instead of writing down the comments for the code that was written months ago. In doing so, will save time and make the documentation precise and complete. Use proper versioning to keep track of all changes in the document.
3. Document any changes to the code. Documenting new features or add-ons is pretty obvious. However, deprecated features should also be documented, capturing any change in the product.
4. Use simple language and proper formatting. Code documents are typically written in English so that any developer could read the comments, regardless of their native language. The best practices for documentation writing require using the Imperative mood, Present tenses, preferably active voice, and second person. Use consistent header, footer, headings, and font sizes for better readability.
5. Combine automated documentation tools and human input. Automation will speed up the process, but a person can make the code documentation comprehensible while adding more of a personal touch.
6. Code and Comments is written for humans

## When Writing Code Comments for documentation

### Better Comments

When making comments for documenting code, the extension
[ Better Comments ](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) should be put into consideration.

The Better Comments extension helps in creating a human-friendly comments into the code.

    Alerts
    Queries
    TODOs
    Highlights
    Commented out code can also be styled to make it clear the code shouldn't be there
    Any other comment styles you'd like can be specified in the settings

With Better comments extension we're able to categorise comments into the following annotation:

- Alerts

        /*
        * ! this is an BLOCK level alert comment.
        */

        // ! This is an INLINE level alert comment
        // ! OH MY GOD, PLEASE avoid doing this

- Queries

        /*
        * ? This is a BLOCK level Query comment for asking questions.
        */

        // ? This is an INLINE level Query comment for asking questions.
        // ? Do I really need to do this anymore?
        // ? or Do I need to want to do this ?

- TODOs

        /*
        * TODO: this is a BLOCK level TODO comment
        */


        //TODO: this is an INLINE level TODO comment
        // Fetch Data from API
        // Display Data received from fetching

- Highlighted

        /*
        * * This is a BLOCK level highlight comment
        */

        // * This is an INLINE level highlight comment
        // * Yep that is indeed an inline highlight comment

### General :

1. Each line of a comment should never be more than 80 characters
2. For inline comments, as much as possible keep the comments 5 lines max.
3. For code blocks try to include the following:
   - @author \WhoMadeThisCode
   - @params \DescriptionOfTheParameters
   - @returns \WhatIsTheReturnedDataOrObject
   - @throws \WhatIsThisExceptionThrown

### Class / Object

**Class Level Variables**

When documenting a class level variable the following should be described.

1. Short description of variable
2. Data Type of variable


       /**
        * The Laravel framework version.
        * @var string
        */
       const VERSION = '5.8.35';

### Function / Method

When documenting a method the following should be described.

1.  A summary of what the method does.
2.  What parameters needed in the method
3.  What does the method return.
4.  If it throws an Exception, what would it throw


         /**
          * Get the path to a versioned Mix file.
          *
          * @param  string  $path
          * @param  string  $manifestDirectory
          * @return \Illuminate\Support\HtmlString|string
          *
          * @throws \Exception
          */
         public function __invoke($path, $manifestDirectory = '')
         {
             static $manifests = [];
             $manifestPath = public_path($manifestDirectory.'/mix-manifest.json');

             if (! isset($manifests[$manifestPath])) {
                 if (! file_exists($manifestPath)) {
                     throw new Exception('The Mix manifest does not exist.');
                 }

                 $manifests[$manifestPath] = json_decode(file_get_contents($manifestPath), true);
             }
             return new HtmlString(app('config')->get('app.mix_url').$manifestDirectory.$manifest[$path]);
         }

### Inline

//TODO:
