## Black Book SSTE Technical Take Home

*This test should not take more than an hour to complete*

The test is broken into three separate parts:
  - knowledge of remote git operation
  - knowledge of API testing
  - knowledge of UI testing
________________
#### Getting Started
* Credentials are passed in plain text in the encrypted email you received.
* Tests can be written in your language of choice however Black Book focuses on JavaScript and Python.
* Tests repository should include a readme with explicit instructions on how to prepare the environment and execute the tests.

> ***DO NOT FORK THIS REPOSITORY***
1. Download this repository as a zip and extract to an empty directory. 
1. Initialize an empty Git repository locally inside the project folder
1. Commit the base, unmodified directory and push to the remote repository of your choice (GitHub, Azure DevOps, GitLab etc.)
1. Commit often to document your methodology and use descriptive commit messages 
> ***MAKE SURE TO PUSH ALL CODE, CODE NOT SUBMITTED CANNOT BE REVIEWED***
>
____

### API Testing
##### The base test url is `https://sste-test.blackbook.com/retailapi/retailapi/`
##### The json_schema is in `retail_schema.json` for reference 
> All relevant code should be placed in the `./api_testing` folder

All API responses are JSON.

Tests may append onto the url.  For example: if a test states that the url is 
`listings` then the full request is 
`https://sste-test.blackbookcloud.com/retailapi/retailapi/listings`.

#### Test Path: `/listings?uvc=2015300726&vin=1FTEW1EF8FFC45951&zipcode=30518`
1. Confirm that the request returns a 200 status code
1. Confirm that `effective_parameters.uvc` exists
1. Iterate through `listings` and using regex verify that `listings[].msrp` is an integer
1. Iterate through `message_list` and verify that `message_list.type` is not `Error`

_____

### UI Testing
##### The base test url is `https://computer-database.herokuapp.com/computers`
> All relevant code should be placed in the `./ui_testing` folder
1. Create a new computer with your choice of `Computer name` and the following data:
    * Computer name:        "[your choice]"
    * Introduced date:      "2020-09-01"
    * Discontinued date:    "2021-09-01"
    * Company:              "Evans & Sutherland"
1. Verify that the computer is created by utilizing the "Filter by name" text box and table
1. Click the `Computer name` and edit the `Discontinued Date` to `2022-09-01`
1. Verify that the modified date is in the table
1. Delete the Computer
1. Verify that the Computer no longer exists in the table
