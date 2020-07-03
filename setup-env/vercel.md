# Deploying With Vercel

It is very easy to deploy simple web sites/apps with [Vercel](https://vercel.com) for free.
Simple here means the website is just made with HTML, CSS, and JavaScript and possibly some assets like image files.
For example, we can deploy:

 - Angular apps

Vercel integrates deeply with GitHub, but it should also be possible to keep the two services separate.

## Vercel Account Signup

The first step is to create a Vercel account by signing up with your GitHub account (it may even be possible to create an account using the CLI see below).
After the account is created you have two options for signing in:

- Sign in using your GitHub account
- Sign in with your email address (the same email address you use for GitHub), instead of a password an email is sent to you containing a link to sign in.

## GitHub Integrated Deployment

From the Vercel dashboard choose to import a project and enter the URL for the GitHub repository.
Now everytime you push to the repo (in any branch) Vercel will automatically build and deploy the pushed commit.

- Note that the free Vercel tier can only integrate with your personal repos, it cannot integrate with repos in GitHub organizations.

## Vercel CLI Deployment (Preferred Method)

Vercel CLI can be used to deploy independently of a GitHub account (GitHub organization repos may also be deployed in this way).

- First install the CLI in your Node project:

    ```bash
    npm install vercel --save-dev
    ```

- Local Node packages cannot be run from the command line without additional configuration.
  One method is to add a script to `package.json`:

    ```json
    ...
    "scripts": {
      "build": "ng build",
      "vercel": "vercel"   // add this line
    },
    ...
    ```

  Now you can run the `vercel` command with

    ```bash
    npm run vercel
    ```

- If you have not already done so build your app.
  For example, to build an Angular app:

    ```bash
    ng build --prod
    ```
  The output will be in placed in the `./dist` folder.

- Login to Vercel with

    ```bash
    npm run vercel login
    ```
  It will ask for your email address, then you will have to click the link in the email sent to you.

- Deploy to Vercel with

    ```bash
    npm run vercel
    ```

  If this is the initial deployment you will need to answer some propmts.
  The most important is to specify `./dist` as the directory containing your code.

- Your app is now deployed and you can run

    ```bash
    npm run vercel logout
    ```
    