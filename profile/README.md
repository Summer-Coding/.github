# Summer Coding

The purpose of this organization is to help 2 new developers learn web development practices and technologies. We will be using React, Redux, Nest.js, Prisma, and Supabase to create a full-stack recipes application for storing and displaying personal recipes.

## Build Status

Web [![CircleCI](https://dl.circleci.com/status-badge/img/gh/Summer-Coding/recipes-web/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/Summer-Coding/recipes-web/tree/main)

Server [![CircleCI](https://dl.circleci.com/status-badge/img/gh/Summer-Coding/recipes-server/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/Summer-Coding/recipes-server/tree/main)

## Setup

### Clone projects

1. create a directory for the projects: `mkdir recipes`
2. cd into new directory: `cd recipes`
3. clone web: `git clone https://github.com/Summer-Coding/recipes-web.git`
4. clone server: `https://github.com/Summer-Coding/recipes-server.git`

### Setup Database

1. install docker: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
2. install scoop:
  1. `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
  2. `irm get.scoop.sh | iex`
3. install Supabase CLI
  1. `scoop bucket add supabase https://github.com/supabase/scoop-bucket.git`
  2. `scoop install supabase`
4. Login to Supabase:
  1. Create an account at [https://app.supabase.com/](https://app.supabase.com/)
  2. Create Access Token at [https://app.supabase.com/account/tokens](https://app.supabase.com/account/tokens)
  3. _**Important**_ Copy token before moving on!!
  4. `supabase login` (paste Access Token when prompted from previous step)
5. Start Supbase local
  1. create directory `mkdir recipes-database` (you can name it whatever you want, but recipes-database makes the most sense to me)
  2. cd into project `cd recipes-database`
  3. init: `supbase init`
  4. start: `supabase start`
  
Note: after last command run, it will print out environment configuration variables required for the Config section below.
  
 ### Project Config:
 
 #### Web
 
1. Change the name of `.env.sample` to just `.env`
2. Update the file:

```env
  REACT_APP_SUPABASE_URL=#API URL
  REACT_APP_SUPABASE_KEY=#anon key
```

#### Server
1. Change the name of `.env.sample` to just `.env`
2. Update the file:

```env
  DATABASE_URL=#DB URL
  SUPABASE_URL=#API URL
  SUPABASE_KEY=#anon key
  SUPABASE_PRIVATE_KEY=#service_role key
  SUPABASE_JWT_SECRET= # is not in printed config - generate a random 32 chracter string.
```

### Launch and Configure Supabase

1. in a termal navigate to `recipes-server` and type `npx prisma db push`
2. Open the `Studio URL` and the `Inbucket URL` printed in your terminal after running `supabase start` in a web browser
3. Copy the code found here: [https://github.com/Summer-Coding/recipes-sql/blob/main/local-setup.sql](https://github.com/Summer-Coding/recipes-sql/blob/main/local-setup.sql)
4. In the Studio tab, navigate to the `SQL Editor` screen (left hand side, looksl ike a terminal window)
5. paste into SQL Editor and click `RUN`

### Run Programs

1. navigate to `recipes-server` in a terminal and type `yarn start:dev`
2. navigate to `recipes-web` in a separate terminal instance and type `yarn start`

### Logging in

1. navigate to [http://localhost:3000/login](http://localhost:3000/login)
2. enter any email and submit
3. open the `Inbucket URL` tab, which intercepts any emails sent from the local supabase instance
4. click on `Monitor` in the navbar
5. click on the email that was just intercpeted (should only be 1 at the moment)
6. In the email, click the `Log In` link

That's it! You have a user and everything is running.

### Create a profile

1. When you are logged in, navigate to [http://localhost:3000/profile](http://localhost:3000/profile)
2. fill out form and click submit
