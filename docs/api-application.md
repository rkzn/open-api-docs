# API Application

To interact with Spotware Opan API you have to first create an API application, you will use the application credentials for accessing the API.

## Creating Application

You can create an API application by following these steps:

1. Go to Spotware Open API web page: [https://connect.spotware.com/](https://connect.spotware.com/)

2. Login with your cTrader ID

3. After logging in go to your applications page: [https://connect.spotware.com/apps](https://connect.spotware.com/apps)

4. Click on "Add New App" button

5. Provide all the detail related to your application by filling the application form

6. Click on Save button

7. Your new created application must appear on your applications list now and its status will be "Submitted"

Now you have an API application but you can't use it right now, because the application status is not active and you have to contact Spotware to activate your API application.

## Activating Application

To activate your application first be sure that your application description field is not empty and it provides good amount of info about your application like what your application will be used for.

Then contact Spotware by sending an email to: <a href="mailto:connect@spotware.com">**connect@spotware.com**</a>

In your email you have to provide your application name and your cTrader ID.

## Adding Redirect URIs

Once your application got activated by Spotware you can start using the Open API through your application, thr next step is to add a redirect URI that will be used for [authentication](../account-authentication).

You can always change your application redirect URIs and add new ones or remove old ones.

!!! note
    The playground default redirect URI is only for playground environment, it will not work outside playground environment, you can't use it on your own code/program.