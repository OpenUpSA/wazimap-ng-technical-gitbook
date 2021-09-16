# GUI Tests

### File structure

* We use Cypress for GUI tests along with Cucumber
* All the GUI tests could be found in `__tests__/gui` folder
* The test steps are in the `.feature` files and the test step definitions are in the `.js` files in the folder that shares the same name as the `.feature` file
  * For example the step definitions of `facility_modal.feature` need to be in the `facility_modal`folder\(name of the js files are not important\)
* We intercept all the requests and respond with local data. The data for each test are kept in json files in the folder of the corresponding test.

### Running the tests

* Start the project
* In a new terminal running `yarn cypress:open` will open the cypress window.
* In the cypress window you can see all the e2e and gui tests and by clicking on any of it you can start testing
* Without opening the cypress window, there are 2 ways to run the gui tests
  * `yarn cypress:gui` runs all the gui tests and saves their result in cypress dashboard
  * `yarn cypress:gui-local` runs all the gui tests without saving anything to the cypress dashboard. While working locally, this script should be used to prevent exceeding dashboard monthly test quota

### Cypress dashboard

* [https://dashboard.cypress.io/](https://dashboard.cypress.io/)
* The credentials for the dashboard could be found in OpenUp general credentials file
* Everytime `cypress:gui` script is run, the test results, logs and their videos are saved to the dashboard. Github actions runs this script too. 
* By selecting `WazimapNG` in the Projects page, all the latest test runs could be viewed.

![Projects page](../.gitbook/assets/image%20%2860%29.png)

![Latest test runs of WazimapNG project](../.gitbook/assets/image%20%2872%29.png)

* By clicking on any of the test runs, you can view
  * Overview : How many tests are failed / passed / skipped.... etc
  * Test results : Details, statuses, result logs... etc
  * Specs : Screenshots, videos... etc

![Analytics](../.gitbook/assets/image%20%2864%29.png)

* More useful details\(Average run duration, Top failures, Slowest tests...\)  could be found in Analytics menu of the dashboard. 

