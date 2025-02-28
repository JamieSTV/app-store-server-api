### [3.5.0] 2023-09-21

**IMPROVEMENTS:**

Missing endpoints added:
- Send Consumption Information
- Extend a Subscription Renewal Date
- Extend Subscription Renewal Dates for All Active Subscribers
- Get Status of Subscription Renewal Date Extensions

### [3.4.1] 2023-09-17

**BUGFIX:**

- `TransactionInfo`: `storefront`, `storefrontId`, and `transactionReason` are now nullable and null by default, in order to be compatible with old notifications
- `RenewalInfo`: `renewalDate` is now null by default, in order to be compatible with old notifications
- `Response\NotificationHistoryResponse`: `paginationToken` presence in response is now optional

### [3.4.0] 2023-09-16

**IMPROVEMENTS:**

- New `notificationType`/`subtype` in `ResponseBodyV2`

### [3.3.2] 2023-09-16

**BUGFIX:**

- ASN1SequenceOfInteger: multiple `00` bytes in the beginning of integer numbers handled when parsing HEX signature representation

### [3.3.1] 2023-09-07

**BUGFIX:**

- `AppMetadata`: `bundleId`, `bundleVersion`, `renewalInfo`, `transactionInfo` and `status` now are `NULL` by default (to prevent `Typed property ... must not be accessed before initialization` error)

### [3.3.0] 2023-09-06

**IMPROVEMENTS:**

- New field implemented
  - `AppMetadata`: `status`

### [3.2.0] 2023-09-03

**IMPROVEMENTS:**

- New fields implemented
  - `RenewalInfo`: `renewalDate`
  - `TransactionInfo`: `storefront`, `storefrontId`, `transactionReason`

### [3.1.1] 2023-09-03

**BUGFIX:**

- `ResponseBodyV2`: `createFromRawNotification()` fix, now it checks incoming notification to be not only a valid JSON, but also to be an array

### [3.1.0] 2023-08-26

**BUGFIX:**
 
- `ASN1SequenceOfInteger`: math fixes
- `StatusResponse`: `data` array initialization with `[]`

**IMPROVEMENTS:**

- `HTTPRequest`: PUT method added; HTTP method and URL added to `HTTPRequestFailed` exception message
- `JWT`: additional information in exception message

### [3.0.1] 2023-08-23

**BUGFIX:**

- Math bug fixed in `ASN1SequenceOfInteger`. In rare cases signature was calculated in a wrong way which led to `Wrong signature` exception in `JWT::verifySignature`

### [3.0.0] 2023-08-18

***BREAKING CHANGES:***

- Main classes renamed:
  - `APIClient` -> `AppStoreServerAPI`
  - `APIClientInterface` -> `AppStoreServerAPIInterface`
  - `Notification\ResponseBodyV2` -> `ResponseBodyV2`
  - `JWT` -> `Util\JWT`
  - `Request\GetTransactionHistory` -> `Request\GetTransactionHistoryRequest`
  - `Request\RequestTestNotification` -> `Request\RequestTestNotificationRequest`
  - `Request\GetTransactionHistoryQueryParams` -> `RequestQueryParams\GetTransactionHistoryQueryParams`
- Environment consts moved out from all classes to the separate class `Environment`
- `getTransactionHistory()` method signature changed: it no longer expects for QueryParams instance as a second arguments, now it expects array instead
- `AppStoreServerAPI` (previously `APIClient`) constructor signature changed:
  - `$environment` argument type changed from int to string
  - `$keyId` and `$key` arguments swapped

**IMPROVEMENTS:**

- PHP 7.4 support out of the box ;)
- A lot of new endpoints (see [README](https://github.com/readdle/app-store-server-api/blob/master/README.md))
- Examples for all implemented endpoints (and notification listener)
