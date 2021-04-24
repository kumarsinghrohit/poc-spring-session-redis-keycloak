# Mosaiq Store PoC for sharing session across services using a centralized repository .

- For the sample to work, Redis 2.8+ must be installed on localhost and run the redis-server on the default port (6379).
- Additionally redis-cli can also be started to run Redis commands.
- Run the docker-compose.yml and export the realm configuration in keycloak.


## What the POC does:
- This POC uses Spring Session to transparently leverage Redis to back the application’s HttpSession.
- Once the application is up and running and the user is logged in, a session is created and stored in redis-server. If we check values
 in Redis-cli(using "keys *" command), we will get our session id.

## NOTE: 
  - The same application can be copied and run by changing the port number in application.properties and adding the uri(http://loccalhost:{port}/*) to 
  Valid Redirect URIs in keycloak client settings. in this way we can create many applications sharing the same keycloak.realm and keycloak.resource.
  - Now we can check values in Redis-cli(using "keys *" command) and we can see that a single sesion ID per user is created for keycloak-Session for all 
  applications.
