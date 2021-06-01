# API Application

To interact with cTrader Open API you first need to create an API application, You will use the application credentials for accessing the API.

## Creating Application

You can create an API application by following these steps:

1. Go to cTrader Open API web page: [https://connect.spotware.com/](https://connect.spotware.com/)

2. Login with your cTrader ID.

3. After logging in go to your applications page: [https://connect.spotware.com/apps](https://connect.spotware.com/apps)

4. Click on "Add New App" button.

5. Provide all the details related to your application by filling the application form, To get your application approved the soonest possible, please provide a detailed description of your application.

6. Click on Save button.

7. Your new created application will appear on your applications list and its status will be "Submitted".

Now your application has been created.

After it is reviewed by Spotware, you will be contacted by email, either confirming the approval or requesting further details about your application. 

## Activating Application

To activate your application first make sure that the description field is not empty and it provides a good amount of info about your application like what your application will be used for.

## Adding Redirect URIs

Once your application gets activated by Spotware, you can start using the Open API through your application.

The next step is to add a redirect URI that will be used for [authentication](../account-authentication).

You can always change your application's redirect URIs and add new ones or remove old ones.

!!! note
    The default redirect URI is only for the playground environment, it will not work outside the playground environment, you can't use it on your own code/program.