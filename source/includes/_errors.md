# Errors

The Coposition API uses the following error codes.
<aside class="notice">
  Most errors will return both an error code a short error message giving further details.
</aside>

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is missing required parameters.
401 | Unauthorized -- Your API key is wrong, a user has not approved you or you need to sign in.
403 | Forbidden -- You do not have access to the specified resource.
404 | Not Found -- The specified resource or endpoint could not be found.
500 | Internal Server Error -- We had a problem with our server. Try again later.
