# Banking System Draft

This is a JavaFX banking assignment starter updated with a SQLite persistence layer. The supplied JavaFX screens now use `BankingService`; the service delegates storage to JDBC repositories. This is a working draft for review, not a claim that the assignment has been tested or submitted.

## Run locally

1. Install JDK 17 or later and Maven.
2. Open this folder as a Maven project and allow Maven to download the dependencies in `pom.xml`.
3. Run `mvn javafx:run` from this folder.
4. The app creates `banking.db` beside the project when it starts and inserts demonstration data only if the customer table is empty.
5. The demonstration login is `admin` / `admin123` or `teller` / `teller123`. These are starter credentials for a classroom demo, not production authentication.

To use a different database file, run with `-Dbanking.db=path/to/file.db`.

## Database and code structure

- `src/main/resources/schema.sql`: customers, accounts, transactions, constraints, and indexes.
- `CustomerDAO`, `AccountDAO`, `TransactionDAO`: JDBC data access.
- `BankingService`: application operations used by the JavaFX controllers.
- `SeedData`: inserts ten sample customer, account, and opening transaction records into a blank database.
- `src/test/java/BankingServiceIntegrationTest.java`: a service-to-database integration flow.

Account balance changes and their transaction history rows are saved in one SQL transaction. Savings accounts reject withdrawals, investment accounts require a P500 opening balance, and monthly interest is credited once per account per calendar month.

## Build and test

Run `mvn test` for the integration test and `mvn javafx:run` to launch the app. Test results must be recorded only after the commands complete successfully in your environment.

## Assignment checks still needed

- The starter model has no customer employment status, so the app can collect employer name/address for cheque accounts but cannot independently prove the customer is employed. Confirm the expected design with your lecturer and add an employment field if required.
- The login remains hardcoded in `LoginManager`; it is not stored or authenticated through SQLite.
- Review all assignment requirements, diagrams, and report wording yourself. The assignment identifies this as individual work. Replace example customer names and addresses with your own clearly synthetic test data if your lecturer expects a different sample dataset.
