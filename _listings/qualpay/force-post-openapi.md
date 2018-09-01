---
swagger: "2.0"
x-collection-name: Qualpay
x-complete: 0
info:
  title: Qualpay Payment Gateway Force transaction approval
  description: Can be used when an online authorization request received a 'declined'
    reason code and the merchant received an authorization from a voice or automated
    response (ARU) system. The required fields are the same as a sale or authorization
    request, except that the expiration date (exp_date) is not required, and the 6-character
    authorization code (auth_code) IS required.
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