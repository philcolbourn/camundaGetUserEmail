# camundaGetUserEmail
Get user's email address using Camunda REST API

Based on [camunda-http-connector-example](https://github.com/rob2universe/camunda-http-connector-example).

There is currently no easy way (that I know of without Java coding) to get a user's email address (same for firstName and lastName).

Camunda REST API allows us to get a user's profile from their user ID:
`http://localhost:8080/engine-rest/user/${userId}/profile`

if `userId="parkerp"` this will return a JSON string like this:
`{"id":"parkerp","firstName":"Pen","lastName":"Parker","email":"pen.parker@example.com"}`

if REST response was placed into a variable `userRecord` then parkerp email address can be extracted with this:
`${S(userRecord).prop("email").stringValue()}`

Then we can send an email using [camunda-bpm-mail](https://github.com/camunda-community-hub/camunda-bpm-mail)
