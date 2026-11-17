# Postman API Testing

I built this project to practice API testing with Postman and JavaScript, starting with introductory course exercises using the public Simple Tool Rental API.

I worked with HTTP methods, JSON responses, authentication, dynamic variables, and automated assertions. I later expanded the original collection to improve test coverage and add new validation scenarios.

## Test Coverage

- API status, tool listing, category filtering, and stock checks.
- Authenticated order lifecycle: create, list, retrieve, update, and delete.
- Automated verification that an updated order comment was saved.
- Negative tests for expected HTTP `404` and `401` responses.
- Dynamic `toolId` and `orderId` values passed between requests.

**V1.0:** Original workflow with basic response assertions and manual update verification.

**V2.0:** Additional assertions, automated update verification, and negative tests.

## Project Files

- [V1.0 Postman Collection](collections/tool-rental-api-v1.0.postman_collection.json)
- [V2.0 Postman Collection](collections/tool-rental-api-v2.0.postman_collection.json)
- [Recorded Test Results](docs/recorded-results.md)

**Tools:** Postman, JavaScript, Newman, Node.js/npm, Newman HTML Extra Reporter, Git, and GitHub.

## Running the Tests

1. Import the V2.0 collection into Postman.
2. Run **Register a new API client** manually using fictional test information. Its script saves the returned token in the collection variable `apiToken`.
3. Clear any old global `toolId` and `orderId` values before a fresh run.
4. Run the collection from **Status** using Postman Collection Runner.

The V2.0 collection contains 13 requests. The automated workflow executes 12 because client registration is performed manually.

To run the collection with Newman, install it with `npm install -g newman` if needed, then execute:

```bash
newman run collections/tool-rental-api-v2.0.postman_collection.json --env-var "apiToken=YOUR_TOKEN"
```

Replace `YOUR_TOKEN` with a valid training API token. The exported collection does not contain a real token. Tokens entered directly in Terminal commands may remain in shell history, so they should never be shared or committed.

## Test Results

| Version | Date | Requests | Assertions Passed | Failures |
|---|---|---:|---:|---:|
| V1.0 | 1 Nov 2026 | 9 | 13 | 0 |
| V2.0 | 6 Nov 2026 | 12 | 25 | 0 |

Both versions passed in **Postman Collection Runner and Newman CLI**.

I also generated HTML Extra reports for local review. These reports are excluded from Git because they may contain authentication details.

See [Recorded Test Results](docs/recorded-results.md) for execution details and historical results.

## Reference

This is an educational project using the [Simple Tool Rental API](https://github.com/vdespa/quick-introduction-to-postman/blob/main/simple-tool-rental-api.md), maintained by Valentin Despa. I did not develop the API itself. Results may vary if the API or its test data changes.
