## LMS Database Setup ()

<hr>

### Production Environment

<hr>

For JustEd, we use `supabase` as our database. It is fast, easy-to-setup and provides a very nice interface.

#### 1. Install `Supabase CLI`

To install `supabase-cli`, refer to this link: https://supabase.com/docs/guides/cli/getting-started

Once installed, you can check on terminal if installation is proper.

```sh
$ supabase --version
1.136.2
```

#### 2. Make a project on Supabase Cloud

Make a project on `supabase.com`'s cloud. Goto the website and create a project. Note _database password_, you will need it in the next step.

> **Note:** Along with database password, also note Project URL, Anon Key and Service Key - you will need these later in setting up the dashboard.

#### 3. Push the migrations

Run the following commands:

```sh
$ supabase login   # This will redirect you to the browser and you shall login.

$ supabase link    # Once logged in, you will see your project's URL here. Select your project here.

$ supabase db push   # This will apply the migrations.
```

You can now go to the supabase dashboard and should be able to see the tables, functions, etc. After every update, you just need to pull the changes from this repo and `db push` the migrations.

#### 4. Add the seed data [Optional]

If you want some data to be present when you first time start your app, you can make use of `seed.sql` data. There is no direct command line way to run this sql file. So you will have to go the project's SQL editor, and run that sql file there.

<hr>

### Development Environment

<hr>

#### 1. Install `Supabase CLI`

To install `supabase-cli`, refer to this link: https://supabase.com/docs/guides/cli/getting-started

Once installed, you can check on terminal if installation is proper.

```sh
$ supabase --version
1.136.2
```

#### 2. Clone this repo and run `supabase start`

That's it. In this repo you need to run `supabase start`. Note: This step depends on `docker`, so keep docker installed beforehand.

```sh
$ docker --version
Docker version 26.1.4, build 5650f9b
```

You will get an output like this:

```sh
$ supabase start
    supabase local development setup is running.

    API URL: http://127.0.0.1:54321
    GraphQL URL: http://127.0.0.1:54321/graphql/v1
    DB URL: postgresql://postgres:postgres@127.0.0.1:54322/postgres
    Studio URL: http://127.0.0.1:54323
    Inbucket URL: http://127.0.0.1:54324
    JWT secret: super-secret-jwt-token-with-at-least-32-characters-long
    anon key: - some long key -
    service_role key: - some long key -
```

Go to the `.env` file of LMS client and put these values.

```env
    PUBLIC_SUPABASE_URL=<API URL>
    PUBLIC_SUPABASE_ANON_KEY=<anon key>
    PRIVATE_SUPABASE_SERVICE_ROLE=<service_role key>
```
<hr>