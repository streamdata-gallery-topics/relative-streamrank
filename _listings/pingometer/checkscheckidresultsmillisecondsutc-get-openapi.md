---
swagger: "2.0"
x-collection-name: Pingometer
x-complete: 0
info:
  title: Checks API Get Checks Results
  description: Gets a specific check result by a numeric java timestamp.
  version: 1.0.0
host: api.pingdom.com
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /alerts/triggered:
    get:
      summary: Triggered Alerts
      description: Get a list of all triggered alerts on your account, per subject
        (device or service) or per alert config.
      operationId: triggered-alerts
      x-api-path-slug: alertstriggered-get
      parameters:
      - in: query
        name: closed
        description: Whether to filter by closed or open alerts - unset = all alerts,
          false = open alerts, true = closed alerts
        type: string
      - in: query
        name: filter
        description: You can provide a JSON encoded hash filter for the search that
          will return items that match the filter
        type: string
      - in: query
        name: subjectType
        description: The type of the subject - device, service, deviceGroup or serviceGroup
          if you also specify the subjectId as part of the URL (see examples below)
        type: string
      - in: query
        name: token
        description: Your API token
        type: string
      responses:
        200:
          description: OK
      tags:
      - Alerts
  ? |2-

        /api/{version}/checks
  : ? |2-

          get
    : summary: Get Check List
      description: Returns a list overview of all checks.
      operationId: |2-

        getApiVersionChecks
      x-api-path-slug: apiversionchecks-get
      parameters:
      - in: query
        name: include_tags
        description: Include tag list for each check
        type: <td>boolean</td>
      - in: query
        name: limit
        description: Limits the number of returned probes to the specified quantity
        type: <td>integer</td>
      - in: query
        name: offset
        description: Offset for listing
        type: <td>integer</td>
      - in: query
        name: tags
        description: Tag list separated by commas
        type: <td>string</td>
      responses:
        200:
          description: OK
      tags:
      - Checks
  '/checks ':
    ' get ':
      summary: Get Checks
      description: Gets a list of all checks that are visible to you as a user or
        a customer depending on the request context.
      operationId: getChecks
      x-api-path-slug: checks-get
      responses:
        200:
          description: OK
      tags:
      - Checks
  /checks/{checkId}/results/{millisecondsUtc}:
    ' get ':
      summary: Get Checks Results
      description: Gets a specific check result by a numeric java timestamp.
      operationId: getChecksCheckResultsMillisecondsutcDetailLevelDetailLevel
      x-api-path-slug: checkscheckidresultsmillisecondsutc-get
      responses:
        200:
          description: OK
      tags:
      - Checks
basePath: /
x-streamrank:
  polling_total_time_average: "0"
  polling_size_download_average: "0"
  streaming_total_time_average: "0"
  streaming_size_download_average: "0"
  change_yes: "0"
  change_no: "0"
  time_percentage: "0"
  size_percentage: "0"
  change_percentage: "200"
  last_run: ~
  days_run: "0"
  minute_run: "0"
---