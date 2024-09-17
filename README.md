# bell-postfix

# API Documentation for Bell Postfix Email Deletion

This API allows users to delete all emails from a specified folder on their mail server. The API requires authentication and supports deleting emails from any folder, specified in lowercase.

## Endpoint

- **URL**: `https://qbwgifercxemswpdjqwehfrde.belldns.com/bell/server/postfix/<server_id>/folder/delete`
- **Method**: `POST`
- **Content-Type**: `application/json`

## Request Parameters

The API accepts a JSON payload with the following parameters:

- **key** (string, required):  
  The API key to authenticate the request. This key should be provided by the system administrator.

- **user** (string, required):  
  The email address of the user whose folder you want to delete emails from.

- **password** (string, required):  
  The password for the provided email account. This is used to authenticate with the IMAP server.

- **folder** (string, required):  
  The name of the folder from which you want to delete all emails. The folder name must be in lowercase (e.g., "inbox", "spam", "trash"). Ensure that the folder name matches exactly how it is labeled on the mail server.

## Request Body Example

    {
        "key": "<api-key>",
        "user": "<email_address>",
        "password": "<pssword<",
        "folder": "chosen_folder"
    }

Example Response

      {
          "status": "success",
          "message": "X emails deleted from the spam folder."
      }

Error Response:

    {
        "status": "error",
        "message": "An error occurred: <error details>"
    }

## Usage Notes

- **API Key**: Ensure that the `key` provided is valid. If the API key is incorrect or missing, the request will be rejected.

- **Folder Names**: All folder names must be provided in lowercase. Common folder names include "inbox", "spam", "trash", etc. The folder name should exactly match the folder on the mail server.

- **Security**: This API requires the user's email password to authenticate with the mail server. Ensure secure transmission of this information by using HTTPS.

- **Rate Limiting**: There may be rate limits on how frequently you can make requests. If you encounter rate limiting errors, please wait before retrying.

## Common Issues

- **Invalid API Key**: Make sure the `key` is correct and hasn't expired.

- **Incorrect Folder Name**: Verify that the folder name is in lowercase and exists on the mail server.

- **Authentication Errors**: Ensure the `user` and `password` are correct and the mail server is accessible.

- **Network Issues**: Ensure your network allows connections to the specified URL.

## Testing the API

- You can test this API using tools like curl or Postman. Here's an example using curl:

      curl -X POST https://qbwgifercxemswpdjqwehfrde.belldns.com/bell/server/postfix/<server_id>/folder/delete \
      -H "Content-Type: application/json" \
      -d '{
          "key": "<api-key>",
        "user": "<email_address>",
        "password": "<pssword<",
        "folder": "chosen_folder"
      }'

Make sure to replace <server_id> with the actual server ID you want to interact with.


