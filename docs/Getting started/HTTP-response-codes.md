---
tags: [Getting Started]
---

# HTTP response codes

Application clients that are using Whispir’s API will receive HTTP response codes in response to every request that is issued.

The table below describes the response codes that will be issued and gives potential reasons for why they may have been sent back.

## Successful response codes

| Response Code             | Meaning                                                                                                                                                                                                                                                  |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200 OK**                | Successful request. <br /><br /> No further action required.                                                                                                                                                                                             |
| **201 Created**           | Successfully created the resource. <br /><br />The requested resource has been successfully created and can be found via the URL in the ‘Location’ header.                                                                                               |
| **202 Accepted**          | Successfully accepted the request for processing. <br /><br />The request has been accepted for processing by the asynchronous processor. The request’s unique identifier can be found via the URL in the ‘Location’ header.                             |
| **204 No Content**        | Successfully processed the request but no content was sent back. <br /><br />The update (PUT) or delete (DELETE) request has been successfully processed and no content was returned from the server.                                                    |
| **301 Moved Permanently** | Successful request but the resource is no longer available at this location. <br /><br />This resource URL should no longer be used. Check the location header of the response and redirect the request there.                                           |
| **302 Found**             | Successful request but the resource is temporarily not available at this location. <br /><br />This resource URL should still be used in future, but for this specific request check the location header of the response and redirect the request there. |
| **304 Not modified**      | Content hasn’t changed since last request. <br /><br />No action required.                                                                                                                                                                               |

## Unsuccessful response codes

| Response Code                  | Meaning                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **400 Bad Request**            | Invalid or missing request parameters. <br /><br />Inspect the request parameters and ensure that all required parameters are supplied. <br /><br />Note the error text in the response and update the request accordingly.                                                                                                                                                                                                                                                                                                                                                              |
| **401 Unauthorized**           | Invalid or no credentials passed in the request. <br /><br />Inspect the authorisation header and ensure that a valid authentication has been provided.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **403 Forbidden**              | Authorisation credentials passed and accepted but the account doesn't have permission. <br /><br />Inspect the authorisation header and ensure that a valid authentication has been provided. <br /><br />Returned when HTTP is used instead of HTTPS. <br /><br />Returned when invalid API key is used. <br /><br />Returned when you have tried to make more API calls than your allowed quota (QPS). Refer to API rate limits.                                                                                                                                                       |
| **404 Not Found**              | The requested URL doesn't exist. <br /><br />The requested resource was not found. <br /><br />Inspect the ID in the URL that was used and ensure that it's valid. <br /><br />Inspect the Accept and Content-Type headers that are being used to make sure they’re correct for the URL that is being requested.                                                                                                                                                                                                                                                                         |
| **405 Method not allowed**     | The requested resource doesn't support the supplied verb. <br /><br />Inspect the HTTP method that was used in the request and ensure that it's valid for the resource being requested.                                                                                                                                                                                                                                                                                                                                                                                                  |
| **415 Unsupported Media Type** | The request was unsuccessful because the requested content type is not supported by the API. <br /><br />The application client can use this response to determine if it's asking for a supported version of a resource. On receiving this response the client can query the developer documentation to determine the appropriate version for the requested resource. <br /><br />In most cases, this is due to the user not supplying the correct Accept or Content-Type header for the requested URL. <br /><br />See [JSON and XML Headers](JSON-and-XML-headers.md) for more details |
| **429 Too many requests**      | Above API quota limits. Returned when you have tried to make more API calls than your allowed quota (QPS). <br /><br />Refer to [API rate limits](Rate-limits-pagination-and-best-practices.md).                                                                                                                                                                                                                                                                                                                                                                                         |
| **422 Unprocessable Entity**   | The request is formed correctly but due to some condition it can’t be processed. For example, email is required and it's not provided in the request. <br /><br />The request did not contain all the information required to perform this method. Check your request for the required fields to be passed in and try again. The offending fields will be specified in the error text of the response.                                                                                                                                                                                   |
| **500 Internal Server Error**  | An internal error occurred when processing the request. Attempt the request again and if the HTTP 500 error re-occurs contact the [Whispir Support Team](mailto:'support@whispir.com').                                                                                                                                                                                                                                                                                                                                                                                                  |
| **501 Method Not Implemented** | The HTTP method being used has not yet been implemented for the requested resource.<br /><br /> The method being used is not implemented for this resource. Check the documentation for the specific resource type.                                                                                                                                                                                                                                                                                                                                                                      |