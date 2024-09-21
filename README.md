
# The Assignment


### Project Setup

**Pre-Requisites**

1. Docker / Podman / any OCI compatible container env
2. docker-compose / podman-compose

**Running the Application**

1. One can simply start the application by executing 
```sh
docker compose up 
```

**Configurations**

By default the existing configurations, i.e., the database name, username, password, etc will be the default values used in the docker compose file. If one wants to use custom values,
1. create a replica of `example.env` file as `.env`
2. edit the config parameters in newly created `.env`
3. run docker compose with `--env-file .env` arg
eg:
```sh
# start with a custom configuration
docker compose --env-file .env up

# alternatively
export $(cat ./.env | xargs)    # export the values to the shell env
docker compose up               # run the compose

```

### Application Routes
As mentioned, there is a reverse-proxy setup in-front of the application (acts as the entrypoint). The proxy routes are as bellow,
1. **port: 8000** - works as an all in one router (contains routes to access all the application endpoints)
    1. **[::]:8000/user** - to access user app
    2. **[::]:8000/orders** - to access orders app
    3. **[::]:8000/products** - to access products app

2. **port: 3000** - pointed exclusively to the user app
3. **port: 4000** - pointed exclusively to the orders app
4. **port: 5000** - pointed exclusively to the products app



### The Assignment Question
```md
About this challenge
General tips
The primary focus of this assignment is to check a candidates ability to solve the
problem and as such the main thing that will be looked at is one’s ability to
complete the assignment rather than the efficiency of the solution. Your end result
does not have to be perfect (if you're stuck on something, please don't spend hours on
it). Do as much as you reasonably can, and simply be prepared to explain your choices
and discuss any places where you were stuck.
To get started, please download the assignment files from [here](https://drive.google.com/file/d/1CCbcbr6sSpRkKg9gedEShZjxSgGlWCqW/view).

ToDo
In the assignment folder you are given the code to 3 separate API’s respectively each
having their own set of routes and function upon their own services. Using the provided
API’s you are expected to the accomplish the following :
  1. All 3 of the API’s work with data from a SQL database, you are to successfully finish
  connecting them to a SQL database (PostgreSQL preferably) running as a
  container and get the API’s functioning properly.
  2. Create a Docker-Compose file that contains all 3 of the API’s as separate services
  along with the PostgreSQL database.
  3. Lastly we expect you to use a Reverse Proxy/ API gateway so that all 3 services
  maybe used from different ports like 3000,4000,5000 respectively.
  Notes

On completion we request you to submit the GitHub repository via mail to us (in
case of a private repository add engineers from our team with proper access).

Please document the steps to run and use the assignment.
Please feel free to reach out to us in case if any questions regarding the
assignment.
In the event more time is required to complete this assignment, please do not
hesitate to reach out to us.

```
