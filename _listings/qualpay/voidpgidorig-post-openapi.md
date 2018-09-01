---
swagger: "2.0"
x-collection-name: Qualpay
x-complete: 0
info:
  title: Qualpay Payment Gateway Void previously authorized transaction
  description: Authorizations can be voided at any time. Captured transactions can
    be voided until the batch is closed.
  version: "1.7"
host: api-test.qualpay.com
basePath: /pg
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /auth:
    post:
      summary: Authorize transaction
      description: An approved transaction will continue to be open until it expires
        or a capture message is received. Authorizations are automatically voided
        if they are not captured within 28 days, although most issuing banks will
        release the hold after 24 hours in retail environments or 7 days in card not
        present environments.
      operationId: Authorization
      x-api-path-slug: auth-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Authorization Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /batchClose:
    post:
      summary: Close batch
      description: This message is used when the timing of the batch close needs to
        be controlled by the merchant rather than relying on the daily automatic batch
        close.
      operationId: batchClose.post
      x-api-path-slug: batchclose-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Batch Close Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /capture/{pgIdOrig}:
    post:
      summary: Capture authorized transaction
      description: A capture message may be completed for any amount up to the originally
        authorized amount.
      operationId: Capture
      x-api-path-slug: capturepgidorig-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Capture Request
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: pgIdOrig
        description: pgIdOrig
      responses:
        200:
          description: OK
      tags:
      - ""
  /credit:
    post:
      summary: Issue credit to cardholder
      description: A non-referenced credit requires that the cardholder data be provided
        in the message. This message is only available during the first 30 days of
        account production activity - the refund message should generally be used
        to return money to the cardholder.
      operationId: Credit
      x-api-path-slug: credit-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Credit Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /force:
    post:
      summary: Force transaction approval
      description: Can be used when an online authorization request received a 'declined'
        reason code and the merchant received an authorization from a voice or automated
        response (ARU) system. The required fields are the same as a sale or authorization
        request, except that the expiration date (exp_date) is not required, and the
        6-character authorization code (auth_code) IS required.
      operationId: Force
      x-api-path-slug: force-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Force Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /refund/{pgIdOrig}:
    post:
      summary: Refund previously captured transaction
      description: Returns money to the cardholder from a previously captured transaction.
        Multiple refunds are allowed per captured transaction, provided that the sum
        of all refunds does not exceed the original captured transaction amount. Authorizations
        that have not been captured are not eligible for refund.
      operationId: Refund
      x-api-path-slug: refundpgidorig-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Refund Request
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: pgIdOrig
        description: pgIdOrig
      responses:
        200:
          description: OK
      tags:
      - ""
  /sale:
    post:
      summary: Sale (Auth + Capture)
      description: This message will perform an authorization of the transaction,
        and if approved will immediately capture the transaction to be included in
        the next batch close. It is used in card present environments, and also card
        not present environments where no physical goods are being shipped.
      operationId: Sale
      x-api-path-slug: sale-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Sale Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /tokenize:
    post:
      summary: Tokenize card
      description: Once stored, a unique card identifier is returned for use in future
        transactions. Optionally, tokenization can be requested in an auth, verify,
        force, credit, or sale message by sending the tokenize field set to true.
      operationId: Tokenize
      x-api-path-slug: tokenize-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Tokenize Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /verify:
    post:
      summary: Verify Card
      description: A verify message will return success if the cardholder information
        was verified by the issuer. If AVS or CVV data is included in the message,
        then the AVS or CVV result code will be returned in the response message.
      operationId: Verify
      x-api-path-slug: verify-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Card Verify Request
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - ""
  /void/{pgIdOrig}:
    post:
      summary: Void previously authorized transaction
      description: Authorizations can be voided at any time. Captured transactions
        can be voided until the batch is closed.
      operationId: Void
      x-api-path-slug: voidpgidorig-post
      parameters:
      - in: body
        name: body
        description: Payment Gateway Void Request
        schema:
          $ref: '#/definitions/holder'
      - in: path
        name: pgIdOrig
        description: pgIdOrig
      responses:
        200:
          description: OK
      tags:
      - ""
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---