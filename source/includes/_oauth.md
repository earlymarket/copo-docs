# Oauth

In order to access a user's data, the user will need to have authorized your application to access their data via oAuth.

You can add oAuth to your app using our <a href="https://github.com/earlymarket/omniauth-coposition-oauth2">ruby gem</a>.

You will need to provide both your API key and an access token associated with the user who's data you are trying to access when using the API. The access token can be included by appending the following query parameter:

<code>?access_token=ACCESS_TOKEN</code>

