# Deploying with Heroku

## First time deployment

1. In the root directory, run `heroku login`
2. Run `heroku create`
  First link is what to navigate to in order to visit the app in the browser. The **second link (the deployment target) is most important**. It is the git repository to push the local server to. Push changes to this remote repository that is managed by Heroku. 
3. Add the remote repo with `git remote add heroku [link]` (this may return with `remote heroku already exists` but that is fine and that means the remote has been successfully created)
4. When you push to this remote repo, it should run through a deployment check, set some runtime configurations, and deploy. (You can test if it was successfully deployed with `heroku open`)

## Subsequent deployments

1. commit
2. push to the heroku remote repo

#### For React
For react, there are two best options for pushing the client build.
##### Option 1 
1. push to heroku
2. Tell Heroku to install **all** dependencies for the client project. This includes development stuff, like webpack and bable. (Even though it's installed, this stuff is never used after the build file is built because the production server will just read the build file. They won't included into the express server or client side files. They won't be loaded into RAM.)
3. Heroku will build the client project
    * Can tell Heroku what to install in the `heroku-postbuild` script (all the client dependencies, including the development ones) 
    * Then tell Heroku it needs to run `npm run build`
##### Option 2 (Most widely used)
Make use of **Continuous Integration (CI)**
1. Push to a 3rd party server CI (an intermediary between the local development and heroku)
2. The CI will run tests and stuff
3. Can configure the CI to build and commit the client to a deployment branch 
4. CI pushes the build to Heroku 

example: circleCI (non-trivial)





## Debugging
* Try running `heroku logs`. It may give error message regarding the deployment process
* http from https. Heroku uses a proxy to determine which server to send users to. Whenever a proxy is used, google often drops the 's' from 'https'. Depending on setup, may be able to set `proxy: true` to enable security.