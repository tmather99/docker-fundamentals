# C:\Windows\System32\drivers\etc\hosts
127.0.0.1       id-local.globomantics.com
127.0.0.1       www-local.globomantics.com

# Application URLs.

* https://www-local.globomantics.com:44395/			-- globomantics.ui
* https://www-local.globomantics.com:44395/api/		-- globomantics.api
* https://id-local.globomantics.com:44395/			-- globomantics.identityserver
* http://localhost:5342/#/events?autorefresh	    -- globoseq
* http://localhost:5010/							-- globosmtp

### globosql host, port
* localhost, 1440

### user/password
* sa/tm@ther99
* globo_dbuser/tm@ther99


### Initial Users
The database creation logic above will create the following users:
* rr@acme.com / `l00neyTunes!`
* wile@acme.com / `l00neyTunes!`
* kim@mars.com / `to1nfinity!`
* stanley@mars.com / `to1nfinity!`

## Preparing Your Workstation for Containers
* [Docker Desktop](https://www.docker.com/products/docker-desktop)
* [Install and Configure Windows Terminal](https://gist.github.com/dahlsailrunner/ec99e195b2a4903748a74df64a1f1a94)
* [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

## SSL With Docker Compose and nginx as Reverse Proxy
https://gist.github.com/dahlsailrunner/679e6dec5fd769f30bce90447ae80081

## Local Kubernetes Setup
Just use the Docker Desktop Kubernetes instance (enable it in Settings within Docker Desktop).

Then here are some handy notes: 
https://gist.github.com/dahlsailrunner/1a47b0e38f6e3ba64d4d61835c73b7e2

## Excluding Health Checks from Serilog Request Logging
Great blog post by Andrew Lock on this very topic:
https://andrewlock.net/using-serilog-aspnetcore-in-asp-net-core-3-excluding-health-check-endpoints-from-serilog-request-logging/
