---
swagger: "2.0"
x-collection-name: Qualpay
x-complete: 0
info:
  title: Qualpay Payment Gateway Close batch
  description: This message is used when the timing of the batch close needs to be
    controlled by the merchant rather than relying on the daily automatic batch close.
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