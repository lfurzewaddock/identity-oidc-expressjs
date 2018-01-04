# identity-oidc-expressjs

An example OIDC service provider to authenticate users with login.gov. Built with Node.js, Express.js, and Passport.js.

This example service provider is configured to run on http://localhost:9393.

## Prerequisites

Install Node.js (version 8.9.3), perhaps using NVM to do so.

Run a [login.gov](https://github.com/18F/identity-idp/) instance locally on port 3000. Note: Passport wants to make various authentication requests to `127.0.0.1:3000`, and when the login.gov instance is run normally at `localhost:3000`, Passport won't be able to find it. A work-around for this issue is to run login.gov using the following command: `rails s -b 0.0.0.0`. However you should note that when login.gov is running in this way, it won't properly allow users to initially set up their LOA3 information. So one work-around is to use a different example client (like [Rails](https://github.com/18F/identity-sp-rails) version) to perform the initial LOA3 authentication, then remember to log-out of that service provider, then subsequent LOA3 authentication attempts from this service provider should work.

## Usage

Install package dependences:

```sh
npm install
```

Run a local webserver:

```sh
DEBUG=identity-oidc-expressjs:* npm start # then view localhost:9393 in a browser
```

![a screencast of a user navigating this application: logging in using LOA1 by clicking a button on the homepage, then getting redirected to a profile page showing the user's email address, then logging out and demonstrating inability to access the profile page again. then repeating the process using LOA3 to log-in produces the same results, except it displays more user information on the profile page.](demo.gif)

## [License](LICENSE)
