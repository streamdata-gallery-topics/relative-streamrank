swagger: "2.0"
x-collection-name: SendGrid
x-complete: 1
info:
  title: SendGrid
  version: 1.0.0
host: api.sendgrid.com
basePath: /v3
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /devices/stats:
    get:
      summary: Get Devices Stats
      description: "**This endpoint allows you to retrieve your email statistics segmented
        by the device type.**\n\n**We only store up to 7 days of email activity in
        our database.** By default, 500 items will be returned per request via the
        Advanced Stats API endpoints.\n\n## Available Device Types\n| **Device** |
        **Description** | **Example** |\n|---|---|---|\n| Desktop | Email software
        on desktop computer. | I.E., Outlook, Sparrow, or Apple Mail. |\n| Webmail
        |\tA web-based email client. | I.E., Yahoo, Google, AOL, or Outlook.com. |\n|
        Phone | A smart phone. | iPhone, Android, Blackberry, etc.\n| Tablet | A tablet
        computer. | iPad, android based tablet, etc. |\n| Other | An unrecognized
        device. |\n\nAdvanced Stats provide a more in-depth view of your email statistics
        and the actions taken by your recipients. You can segment these statistics
        by geographic location, device type, client type, browser, and mailbox provider.
        For more information about statistics, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/index.html)."
      operationId: devices.stats.get
      x-api-path-slug: devicesstats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the statistics
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: How many results to include on each page
      - in: query
        name: No Name
      - in: query
        name: offset
        description: How many results to exclude
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Devices
      - Stats
  /categories/stats:
    get:
      summary: Get Categories Stats
      description: |-
        **This endpoint allows you to retrieve all of your email statistics for each of your categories.**

        If you do not define any query parameters, this endpoint will return a sum for each category in groups of 10.

        Categories allow you to group your emails together according to broad topics that you define. For more information, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/categories.html).
      operationId: categories.stats.get
      x-api-path-slug: categoriesstats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the statistics
      - in: query
        name: categories
        description: The individual categories that you want to retrieve statistics
          for
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: The number of results to include
      - in: query
        name: No Name
      - in: query
        name: offset
        description: The number of results to skip
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Categories
      - Stats
  /campaigns:
    get:
      summary: Get Campaigns
      description: |-
        **This endpoint allows you to retrieve a list of all of your campaigns.**

        Returns campaigns in reverse order they were created (newest first).

        Returns an empty array if no campaigns exist.

        For more information:

        * [User Guide > Marketing Campaigns](https://sendgrid.com/docs/User_Guide/Marketing_Campaigns/index.html)
      operationId: GET_campaigns
      x-api-path-slug: campaigns-get
      parameters:
      - in: query
        name: limit
        description: The number of results you would like to receive at a time
      - in: query
        name: offset
        description: The index of the first campaign to return, where 0 is the first
          campaign
      responses:
        200:
          description: OK
      tags:
      - Email
      - Campaigns
  /alerts:
    get:
      summary: Get Alerts
      description: "**This endpoint allows you to retieve all of your alerts.**\n\nAlerts
        allow you to specify an email address to receive notifications regarding your
        email usage or statistics. \n* Usage alerts allow you to set the threshold
        at which an alert will be sent.\n* Stats notifications allow you to set how
        frequently you would like to receive email statistics reports. For example,
        \"daily\", \"weekly\", or \"monthly\".\n\nFor more information about alerts,
        please see our [User Guide](https://sendgrid.com/docs/User_Guide/Settings/alerts.html)."
      operationId: GET_alerts
      x-api-path-slug: alerts-get
      parameters:
      - in: header
        name: Authorization
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Alerts
  /stats:
    get:
      summary: Get Stats
      description: |-
        **This endpoint allows you to retrieve all of your global email statistics between a given date range.**

        Parent accounts will see aggregated stats for their account and all subuser accounts. Subuser accounts will only see their own stats.
      operationId: GET_stats
      x-api-path-slug: stats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the statistics
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: The number of results to return
      - in: query
        name: No Name
      - in: query
        name: offset
        description: The point in the list to begin retrieving results
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Stats
  /suppression/bounces:
    get:
      summary: Get Suppression Bounces
      description: "**This endpoint allows you to retrieve all of your bounces.**\n\nA
        bounced email is when the message is undeliverable and then returned to the
        server that sent it.  \n\nFor more information see: \n\n* [User Guide > Bounces](https://sendgrid.com/docs/User_Guide/Suppressions/bounces.html)
        for more information\n* [Glossary > Bounces](https://sendgrid.com/docs/Glossary/Bounces.html)"
      operationId: suppression.bounces.get
      x-api-path-slug: suppressionbounces-get
      parameters:
      - in: header
        name: Accept
      - in: query
        name: end_time
        description: Refers end of the time range in unix timestamp when a bounce
          was created (inclusive)
      - in: query
        name: No Name
      - in: query
        name: start_time
        description: Refers start of the time range in unix timestamp when a bounce
          was created (inclusive)
      responses:
        200:
          description: OK
      tags:
      - Email
      - Suppression
      - Bounces
  /suppression/blocks:
    get:
      summary: Get Suppression Blocks
      description: |-
        **This endpoint allows you to retrieve a list of all email addresses that are currently on your blocks list.**

        There are several causes for [blocked](https://sendgrid.com/docs/Glossary/blocks.html) emails: for example, your mail server IP address is on an ISP blacklist, or blocked by an ISP, or if the receiving server flags the message content.

        For more information, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Suppressions/blocks.html).
      operationId: suppression.blocks.get
      x-api-path-slug: suppressionblocks-get
      parameters:
      - in: query
        name: end_time
        description: Refers end of the time range in unix timestamp when a blocked
          email was created (inclusive)
      - in: query
        name: limit
        description: Limit the number of results to be displayed per page
      - in: query
        name: No Name
      - in: query
        name: offset
        description: The point in the list to begin displaying results
      - in: query
        name: start_time
        description: Refers start of the time range in unix timestamp when a blocked
          email was created (inclusive)
      responses:
        200:
          description: OK
      tags:
      - Email
      - Suppression
      - Blocks
  /mailbox_providers/stats:
    get:
      summary: Get Mailbox Provers Stats
      description: |-
        **This endpoint allows you to retrieve your email statistics segmented by recipient mailbox provider.**

        **We only store up to 7 days of email activity in our database.** By default, 500 items will be returned per request via the Advanced Stats API endpoints.

        Advanced Stats provide a more in-depth view of your email statistics and the actions taken by your recipients. You can segment these statistics by geographic location, device type, client type, browser, and mailbox provider. For more information about statistics, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/index.html).
      operationId: mailbox_providers.stats.get
      x-api-path-slug: mailbox-providersstats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the stats
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: The number of results to include on each page
      - in: query
        name: mailbox_providers
        description: The mail box providers to get statistics for
      - in: query
        name: No Name
      - in: query
        name: offset
        description: The number of results to exclude
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Mailbox
      - Provers
      - Stats
  /geo/stats:
    get:
      summary: Get Geo Stats
      description: |-
        **This endpoint allows you to retrieve your email statistics segmented by country and state/province.**

        **We only store up to 7 days of email activity in our database.** By default, 500 items will be returned per request via the Advanced Stats API endpoints.

        Advanced Stats provide a more in-depth view of your email statistics and the actions taken by your recipients. You can segment these statistics by geographic location, device type, client type, browser, and mailbox provider. For more information about statistics, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/index.html).
      operationId: geo.stats.get
      x-api-path-slug: geostats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How you would like the statistics to be grouped
      - in: query
        name: country
        description: The country you would like to see statistics for
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: How many results to include on each page
      - in: query
        name: No Name
      - in: query
        name: offset
        description: How many results to exclude
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Geo
      - Stats