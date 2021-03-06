
# API

### Servey: Class
Inherits Events and returns a server instance.
- `options: Object`
	- `tools: Array` A list of tools that will be available in the handlers.
	- `port: Number` port to use (default: `0`)
	- `cors: Boolean, Object` cors mode (defaults: `false`)
		- `origin: String` Access-Control-Allow-Origin
		- `methods: String` Access-Control-Allow-Methods
		- `headers: String` Access-Control-Allow-Headers
		- `requestMethod: String` Access-Control-Request-Method
	- `host: String` host to use (default: `0.0.0.0`)
	- `secure: Boolean` http or https (default: `false`)
	- `debug: Boolean` sends error message (default: `false`)
	- `event: Object`
		- `handler: Object, AsyncFunction` if function it will be a invoked before and after
			- `before: AsyncFunction` invoked before the handler
			- `after: AsyncFunction` invoked after the handler
	- `routes: Array`
		- `route: Object`
			- `options: Object`
				- `auth: Object`
					- `tool: String` A `Servey.tool` requires the following properties to be available.
						- `toked` Third party tool for jwt tokens.
						- `basic` Builtin tool for basic auth.
						- `session` Builtin tool for session auth.
					- `realm: String` The value for the WWW-Authentication realm header. This will override the `tool` option.
					- `scheme: String` Cookie or any HTTP Authorization header such as Basic or Bearer. This will override the `tool` option.
					- `validate: String, Function`  A name to a `Servey.tool`. Must return an Object with a `valid: Boolean` and `credential: Object` property. This will override the `tool` option.
					- `strategy: String, Function` A name to a `Servey.tool`. Must return an Object with a `valid: Boolean` and `credential: Object` property. This will override the `tool` option.
			- `handler: AsyncFunction`
				- `context: Object`
					- `body: Any`
					- `tool: Object`
					- `code: Number` (default: 200)
					- `head: Object`
					- `query: Object`
					- `method: String`
					- `url: Object` Url
					- `credential: Object`
					- `request: Class` Http.ServerRequest
					- `response: Class` Http.ServerResponse
					- `instance: Class` Servey
- `open: AsyncFunction` Starts listening.
- `close: AsyncFunction` Stops listening.
- `on: Function`
	- `open: Event`
	- `close: Event`
	- `error: Event`
	- `request: Event`
	- `response: Event`

### Servey.tools: Array
Default server tools.
- `static` Static file and single page application.
    - `code: Number` overwrites status code
	- `spa: Boolean` spa mode (defaults: `false`)
	- `folder: String` path to (defaults: `./public`)
	- `file: String` path to default file (default: `index.html`)
