# Deploying With Heroku

[Heroku](https://www.heroku.com) is fairly easy to get setup and running.
First you will need to create an account with Heroku.
There is a free account level which includes the option to use a PostgreSQL database for limited data storage.

## Spring Boot Java App

- Install Heroku CLI with `Ubuntu Software` or `snap`.
- Change to the project directory
- login to heroku account from terminal:

    ```bash
    heroku login -i
    ```

- Create empty application on Heroku along with a remote Heroku Git repository:

    ```bash
    heroku create
    git remote -v
    ```

- Create new Git branch for deployment

    ```bash
    git checkout -b deploy
    ```

- Add a file called `system.properties` to the root directory of the project with the following line to configure the JDK version.

    ```
    java.runtime.version=14
    ```

- Deploy the app to Heroku by pushing the local deploy branch to the master branch of the remote heroku git repository.

    ```bash
    git push heroku deploy:master
    ```

- If the Spring Boot app uses a MySQL database, then you will need a Heroku addon.
  There seem to be two options ClearDB and JawsDB before either can be added you must verify your Heroku account by adding a credit card even though both have free plans.

    ```bash
    heroku addons:create cleardb:ignite
    ```

  Another option is to switch over to using a Postgres database instead.
  The Heroku Postgres addon can be used without verifying your heroku account.

    ```bash
    heroku addons:create heroku-postgresql
    ```

- To redeploy after making changes simply commit the changes to the `deploy` branch and push to the remote heroku master.

    ```bash
    git push heroku deploy:master
    ```
