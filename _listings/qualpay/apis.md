---
name: Qualpay
x-slug: qualpay
description: We provide an omnichannel payments platform, easily adaptable to individual
  needs, whether you are a business, a developer or a partner including Independent
  Sales Organizations (ISO) and Independent Software Vendor (ISV). Our fully-integrated
  payments platform combines a merchant account with a payment solution and reporting
  that todays businesses require.
image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
x-kinRank: "7"
x-alexaRank: "0"
tags: Qualpay
created: "2018-08-31"
modified: "2018-08-31"
url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/apis.md
specificationVersion: "0.14"
apis:
- name: Qualpay Payment Gateway - Authorize transaction
  x-api-slug: auth-post
  description: An approved transaction will continue to be open until it expires or
    a capture message is received. Authorizations are automatically voided if they
    are not captured within 28 days, although most issuing banks will release the
    hold after 24 hours in retail environments or 7 days in card not present environments.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/auth-post-openapi.md
- name: Qualpay Payment Gateway - Close batch
  x-api-slug: batchclose-post
  description: This message is used when the timing of the batch close needs to be
    controlled by the merchant rather than relying on the daily automatic batch close.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/batchclose-post-openapi.md
- name: Qualpay Payment Gateway - Capture authorized transaction
  x-api-slug: capturepgidorig-post
  description: A capture message may be completed for any amount up to the originally
    authorized amount.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/capturepgidorig-post-openapi.md
- name: Qualpay Payment Gateway - Issue credit to cardholder
  x-api-slug: credit-post
  description: A non-referenced credit requires that the cardholder data be provided
    in the message. This message is only available during the first 30 days of account
    production activity - the refund message should generally be used to return money
    to the cardholder.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/credit-post-openapi.md
- name: Qualpay Payment Gateway - Force transaction approval
  x-api-slug: force-post
  description: Can be used when an online authorization request received a 'declined'
    reason code and the merchant received an authorization from a voice or automated
    response (ARU) system. The required fields are the same as a sale or authorization
    request, except that the expiration date (exp_date) is not required, and the 6-character
    authorization code (auth_code) IS required.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/force-post-openapi.md
- name: Qualpay Payment Gateway - Refund previously captured transaction
  x-api-slug: refundpgidorig-post
  description: Returns money to the cardholder from a previously captured transaction.
    Multiple refunds are allowed per captured transaction, provided that the sum of
    all refunds does not exceed the original captured transaction amount. Authorizations
    that have not been captured are not eligible for refund.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/refundpgidorig-post-openapi.md
- name: Qualpay Payment Gateway - Sale (Auth + Capture)
  x-api-slug: sale-post
  description: This message will perform an authorization of the transaction, and
    if approved will immediately capture the transaction to be included in the next
    batch close. It is used in card present environments, and also card not present
    environments where no physical goods are being shipped.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/sale-post-openapi.md
- name: Qualpay Payment Gateway - Tokenize card
  x-api-slug: tokenize-post
  description: Once stored, a unique card identifier is returned for use in future
    transactions. Optionally, tokenization can be requested in an auth, verify, force,
    credit, or sale message by sending the tokenize field set to true.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/tokenize-post-openapi.md
- name: Qualpay Payment Gateway - Verify Card
  x-api-slug: verify-post
  description: A verify message will return success if the cardholder information
    was verified by the issuer. If AVS or CVV data is included in the message, then
    the AVS or CVV result code will be returned in the response message.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/verify-post-openapi.md
- name: Qualpay Payment Gateway - Void previously authorized transaction
  x-api-slug: voidpgidorig-post
  description: Authorizations can be voided at any time. Captured transactions can
    be voided until the batch is closed.
  image: http://kinlane-productions.s3.amazonaws.com/api-evangelist-site/company/logos/qualpay.png
  humanURL: http://qualpay.com
  baseURL: https://api-test.qualpay.com//pg
  tags: Payments, Relative Data, Service API, Webhook Implementations
  properties:
  - type: x-openapi-spec
    url: https://raw.githubusercontent.com/streamdata-gallery-organizations/qualpay/master/_listings/qualpay/voidpgidorig-post-openapi.md
x-common:
- type: x-api-gallery
  url: http://public.transport.victoria.timetable.api.gallery.streamdata.io
- type: x-api-stack
  url: http://qualpay.stack.network
- type: x-developer
  url: https://www.qualpay.com/developer/
- type: x-webhook
  url: https://www.qualpay.com/developer/api/webhooks/get-events
- type: x-website
  url: http://qualpay.com
include: []
maintainers:
- FN: Kin Lane
  x-twitter: apievangelist
  email: info@apievangelist.com
---