# Authentication

```http
POST /api/<version>/<request> HTTP/1.1
X-Engine-Id: <x-engine-id>
X-Engine-Secret: <x-engine-secret>
Content-Type: application/json

{ "PAYLOAD" : "YOUR PAYLOAD" }
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{ "RESULT" : "RESULT OF REQUEST" }
```

```shell
$ curl "http://<domain>/api/<version>/<request>"
	-H "X-Engine-Id: <x-engine-id>"
	-H "X-Engine-Secret: <x-engine-secret>"
```

```shell
$ { "RESULT" : "RESULTS OF REQUEST" }
```

> Make sure to replace `domain`, `x-engine-id` and `x-engine-secret` with your domain, consumer id and consumer secret respectiveley.

Observations has an application security which needs to be passed everytime there is a request. This is to determine where the requests are coming from.

### Needed Headers
Get this secrets from the administrator.

1. `X-Engine-Id: <consumer-id>`
2. `X-Engine-Secret: <consumer-secret>`

### API Endpoint
These are the variables for each endpoints. Example:

1. `<version>: v1`
2. `<requetst>: /observations`
3. `<domain>: devdubai101.schoolimprovement.com`

<aside class="notice">
	You must replace <code>consumer-id</code> and <code>consumer-secret</code>with the given Consumer id and secret respectiveley.
</aside>

## Login

> To login, use this code enter loginName and password:

```http
POST /api/v1/legacy/authenticate HTTP/1.1
X-Engine-Id: <x-engine-id>
X-Engine-Secret: <x-engine-secret>
Content-Type: application/json

{
	"loginName" : "testfoo",
	"password"  : "testfoo"
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message" : "Created session",
	"payload" : {
		"sessionToken ": "MzJiNGM4ZWVkMjgxMjY0ZTdmYjQ1YWUwMGE0ZTBkN2ZkMTA4YzA3MDVhMzQwNzI3MTBiNDk4ZDc2ZDU2ZjY1NQ==",
		"data": {
			"PersonnelId"  : 13778,
			"ClientId"     : 396466,
			"EmailAddress" : "saudia.tepace@globalzeal.net",
			"FirstName"    : "Test",
			"LastName"     : "Foo"
		}
	}
}
```

```shell
# With shell, you can just pass the correct header with each request
curl "http://<domain>/api/v1/legacy/authenticate"
	-H "X-Engine-Id: <x-engine-id>"
	-H "X-Engine-Secret: <x-engine-secret>"
	--data "loginName=<username>&password=testfoo"
```

This endpoint will login the user and return the bearer token.

### Attributes

Attribute | Description
--------- | -----------
sessionToken | Bearer token used for accessing the api
data | user details

### Login user
`POST /api/v1/legacy/authenticate`

Attribute | Description
--------- | -----------
loginName | username of user
password  | password of user

