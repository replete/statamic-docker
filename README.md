# Shinsenter Docker image test case

This repo exists because there are some issues with glide images out of the box with Statamic 5 using this docker image.

## Running

We'll use npm scripts from `/statamic` folder (`cd statamic`) to control the server:

`npm run http {up|down|build|...}` controls http://localhost version
`npm run https {up|down|build|...}` starts the https://localhost version
`npm run https-half {up|down|build|...}` starts the https://localhost version with `half` caching strategy enabled
`npm run https-full {up|down|build|...}` starts the https://localhost version with `full` caching strategy enabled


# https

`npm run devcerts` will create `localhost.key` and `localhost.crt` using mkcert. For SSL to work properly you'll need to install [mkcert](https://github.com/FiloSottile/mkcert) and follow its instructions to install the localhost root certificate. If you are using something else to handle this, generate keys and put them in the root.


## Relevant files
- Default environment variables are at `/statamic/.env`
	- `APP_ENV` = `production` or `local` (dev)
	- `APP_DEBUG` = `false` (true shows laravel debug bar)
	- `STATAMIC_STATIC_CACHING_STRATEGY` = `null` (`half` partially caches, `full` is full static html mode which requires a change to `statamic/cp/assets.php` and some new rewrite rules in nginx.conf to work properly)
- Homepage view template is at `/statamic/resources/views/home.antlers.html`

# username/password
- user: `statamic@local`
- password: `statamic`
