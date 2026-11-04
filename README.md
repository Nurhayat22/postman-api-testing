# Postman API Testing: JSONPlaceholder

A beginner QA practice project where I tested a REST API with Postman. I sent GET, POST, and DELETE requests, checked status codes and JSON responses, and wrote automated tests for each request.

**API under test:** [JSONPlaceholder](https://jsonplaceholder.typicode.com), a free fake REST API for testing and learning.

## What I tested

| ID | Request | Expected result | Status |
|----|---------|-----------------|--------|
| TC-01 | `GET /posts/1` | Status 200, response `id` equals 1 | Passed |
| TC-02 | `GET /posts/99999` (non-existent post) | Status 404 | Passed |
| TC-03 | `POST /posts` with a JSON body | Status 201, response contains the sent `title` and a new `id` | Passed |
| TC-04 | `DELETE /posts/1` | Status 200 | Passed |

Both positive cases (valid request) and a negative case (non-existent resource) are covered.

## Automated tests

Each request has tests written in the Postman **Scripts → After response** tab, for example:

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Response has id = 1", function () {
    const json = pm.response.json();
    pm.expect(json.id).to.eql(1);
});
```

Result of running the whole collection with the Collection Runner: **7 tests passed, 0 failed.**

## How to run

1. Install [Postman](https://www.postman.com/downloads/).
2. Download the collection file (`JSONPlaceholder API Tests.postman_collection.json`) from this repository.
3. In Postman click **Import** and select the file.
4. Right-click the collection and choose **Run collection**.

## What I practiced

- REST API basics and HTTP methods (GET, POST, DELETE)
- HTTP status codes (200, 201, 404)
- Reading and writing JSON
- Writing automated tests in Postman (`pm.test`, `pm.expect`)
- Positive and negative test scenarios
- Running a collection with the Collection Runner

- ## Manual test cases

Besides API testing, this repository includes manual test cases for the login page of the SauceDemo practice website (https://www.saucedemo.com):

- File: `SauceDemo_Login_Test_Cases.pdf` (5 test cases)
- Covered scenarios: valid login, wrong password, empty username, empty password, locked-out user
- Each test case contains: ID, name, precondition, steps, test data, expected result, actual result, and status

## Notes

JSONPlaceholder is a fake API: it returns realistic responses but does not actually save or delete data. For example, a post created with POST cannot be fetched afterwards with GET. This is expected behavior for this API and is not treated as a bug.

## Author

Nurhayat Asgarova, aspiring QA engineer
