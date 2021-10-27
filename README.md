# Tutorial: Deploying a basic Laravel app on Jekyo

Demo app [here](https://laravel-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Laravel app

You can start your Laravel project by using `jekyo create`

Using the **arrows** on your keyboard, select **laravel** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ laravel A basic starter app using [Laravel](https://laravel.com/)
```
When prompted, enter the desired name for your Laravel app. 

`Application name?: laravel-tutorial`

This will create a basic Laravel app in the current directory by cloning this [Laravel starter app](https://github.com/jekyo/laravel-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Laravel app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd laravel-tutorial`

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://laravel-tutorial.jekyo.app ... OK
```

You can now browse to your Laravel app on https://laravel-tutorial.jekyo.app (replace 'laravel-tutorial' with your app name)

## 2. Deploying an existing Laravel app

Navigate to your local Laravel app directory

`cd my-laravel-app`



### Edit package.json

In your _package.json_ file, add a **"start"** line in **"scripts"** and include Jekyo's port and host variables:

```
"scripts": {
    ...
    ...
    ...
    "start": "mix --production --port=$PORT --host=$HOST"
}
```
### .htaccess

**In the root directory** of your app (not in the _public_ folder), create a file named `.htaccess` with the following code: 

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteRule ^(.*)$ public/$1 [L]
</IfModule>
```

### 

Initialize a git repository if you haven't already done so by running `git init`. 

```
git init
git add .
git commit -m "initial commit"
```

If you were already working in a git repository, commit your changes:

```
git add package.json
git add .htaccess
git commit -m "your commit message"
```

### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-laravel-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-laravel-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-laravel-app
```
### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-laravel-app.jekyo.app ... OK
```

You can now browse to your Laravel app on https://my-laravel-app.jekyo.app (replace 'my-laravel-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 