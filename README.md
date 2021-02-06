Part One: 
    Database- psql < jobly-schema.sql
              psql < jobly-seed.sql

    Run jest -i

    beforeEach and afterEach methods:
        beforeEach(BEGIN) initializes each postgres transaction
        afterEach(ROLLBACK) if there is an error thrown because of the
            transaction, postgres will not allow another transaction until
            the offending one has been rolled back.


    create non-admin:
        username: "u-new",
          firstName: "First-new",
          lastName: "Last-newL",
          password: "password-new",
          email: "new@email.com",
          isAdmin: false,

    authorize:
        username: "u-new",
        firstName: "First-new",
        lastName: "Last-newL",
        email: "new@email.com",
        isAdmin: false,

    create admin:
          username: "u-new",
          firstName: "First-new",
          lastName: "Last-newL",
          password: "password-new",
          email: "new@email.com",
          isAdmin: true

    authorize:
        username: "u-new",
        firstName: "First-new",
        lastName: "Last-newL",
        email: "new@email.com",
        isAdmin: true,

First Task: sqlForPartialUpdate (helpers/sql)
    Explained what was going on with the sqlforPartialUpdate function.
    It takes js and turns into sql column names!

    Wrote test code to ensure that it works!

Part Two: Companies

    Add Filtering! (companies.js)

    filtered with min and max employees!
    namelike?

Part Three: Change Authorization

    Want to create, update or delete companies or users? ensureAdmin in middleware/auth checks to see if user is an admin before this is possible.
    expressError throws Unauthorized error! checks to see if isAdmin is True

Part Four:

    Added model for jobs






    Flows!!


    Authenticate:
    

    POST /auth/token
            Works:
        {
          username: "u1",
          password: "password1",
        }

            Unauth with non-existent user:
        {
          username: "no-such-user",
          password: "password1",
        }
            Unauth with wrong password:
        {
          username: "u1",
          password: "nope",
        }
            Bad request with missing data:
        {
          username: "u1",
        }
            Bad request with invalid data:
        {
          username: 42,
          password: "above-is-a-number",
        }
    
    POST /auth/register
            Works:
        {
          username: "new",
          firstName: "first",
          lastName: "last",
          password: "password",
          email: "new@email.com",
        }
            Bad request with missing fields:
        {
          username: "new",
        }
            Bad request with invalid data:
        {
          username: "new",
          firstName: "first",
          lastName: "last",
          password: "password",
          email: "not-an-email",
        }           

        

    Companies:

    

    Jobs:

    Users: