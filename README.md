# Admin Dashboard

# Pre-requisite :

- Install Nodejs v20.11.1
- install npm v10.2.4

## Follow the cammond to setup the environment :

```shell
# clone the Repository

   git clone https://github.com/objex/rabbito-crm.git
```

```shell
# install npm package v10.2.4

   npm install
```

```shell
# install axios package v1.6.8

  npm install axios
```

```shell
# install Firebase package v13.5.2

  npm install -g firebase-tools

```

```shell
# install react dom package v18.2.0

  npm i react-dom
```

```shell
# install react router dom package v6.22.3

  npm i react-router-dom@6.3.0
```

```shell
# install react scripts package v5.0.1

  npm i react-scripts
```

## Quick start

Use the shell script to install node packages and start

```shell
    # Installs node packages and start
   ./start.sh
```

Your site will be running at `http://localhost:3000`!

## Deploy

Deploy project to https://rabbito-app.web.app/

```shell
   # deploys the app
   ./deploy.sh
```

## Refrences:

## Technologies for Building the Software:

- node version 20.3.1. Download link: https://nodejs.org/dist/v20.11.1/node-v20.11.1.tar.gz
- npm version 10.2.4. Download link: https://nodejs.org/en/download
- axios version 1.6.8. Download link: https://www.npmjs.com/package/axios/v/0.27.2
- firebase version 13.5.2. Download link: https://www.npmjs.com/package/firebase-tools/v/9.9.0
- react version 18.2.0. Download link: https://github.com/facebook/react/releases
- react-dom version 18.2.0. Download link: https://www.npmjs.com/package/react-dom/v/18.2.0
- react-router-dom version 6.3.0. Download link: https://www.npmjs.com/package/react-router-dom/v/6.3.0
- react-scripts version 5.0.1. Download link: https://www.npmjs.com/package/react-scripts

#

# CRM API

<details><summary>CRM API</summary>
    <details>
    <summary>Saved Lead</summary>
    <p>Request : </p>
    <pre> 
curl --location --request POST 'https://api.nonprod.rabbito.io/crm' \
--header 'x-api-key: f0YZw18wQNPtEKFunapC8Q5S3lWUtam1FVzjDIcf' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "mazhar@objex.tech",
    "status": "NEW",
    "source": "rabbito",
    "question": "Hello World",
    "comment": "Random",
    "type": "lead" // optional for lead for note use "note"
}'
    </pre>
    <p>Response : </p>
    <pre>
    {
    "message": "Successful"
    }
    </pre>
    </details>
     <details>
    <summary>Update Lead</summary>
    <p>Request : </p>
    <pre>
curl --location --request PUT 'https://api.nonprod.rabbito.io/crm' \
--header 'x-api-key: f0YZw18wQNPtEKFunapC8Q5S3lWUtam1FVzjDIcf' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "mazhar@objex.tech",
    "status": "SALES",
    "source": "rabbito",
    "type": "lead" // optional for lead for note use "note" also noteId
}'
    </pre>
    <p>Response</p>
    <pre>
    {
    "message": "Successful"
    }
    </pre>
    </details>
     <details>
    <summary>Verify Lead</summary>
      <p>Request : </p>
      <pre>
curl --location --request POST 'https://api.nonprod.rabbito.io/crm/verify' \
--header 'x-api-key: {{crm-x-api-key}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "kawsar@objex.tech",
    "source": "rabbito",
    "type": "lead" // by default lead for external use, use "potentialLead" and remove source
}'
      </pre>
      <p>Response : </p>
      <pre>
      {
    "message": "Successful",
    "version": {
        "v": "More-(1.2.1098)",
        "doc": "https://api-docs.emailhippo.com/en/latest/"
    },
    "meta": {
        "lastModified": "Wed, 06 Sep 2023 06:28:27 GMT",
        "expires": "Mon, 04 Mar 2024 06:28:27 GMT",
        "email": "kawsar@unknown.tech",
        "tld": "tech",
        "domain": "unknown.tech",
        "subDomain": null,
        "user": "kawsar",
        ...
    },
    ...
    "hippoTrust": {
        "score": 0,
        "level": "Low"
    },
    "social": {
        "gravatar": {
            "imageUrl": "//www.gravatar.com/avatar/dc8a85b1da18a38682cdba9f5bad44c3",
            "profileUrl": "//www.gravatar.com/dc8a85b1da18a38682cdba9f5bad44c3"
        }
    },
    "domain": null,
    ...
}
      </pre>
    </details>

  <details>
    <summary>Get Leads by Email</summary>
    <p>Request : </p>
    <pre>
curl --location 'https://api.nonprod.rabbito.io/crm/{email}?source=rabbito' \
--header 'x-api-key: {{crm-x-api-key}}' \
--data ''
    </pre>
    <p>Response</p>
    <pre>
    {
    "message": "Successful",
    "kawsar@objex.tech": {
        "data": [
            {
                "comment": "Hello World",
                "created_at": {
                    "_seconds": 1692868734,
                    "_nanoseconds": 546000000
                }
            },
            {
                "comment": "Second comment",
                "name": "Kawsar Hossain",
                "created_at": {
                    "_seconds": 1692868754,
                    "_nanoseconds": 967000000
                }
            }
        ]
    }
}
    </pre>
    </details>
    <details>
    <summary>Get Paginated Leads</summary>
    <p>Request : </p>
    <pre>
curl --location 'https://api.nonprod.rabbito.io/crm?source=rabbito' \
--header 'x-api-key: {{crm-x-api-key}}' \
--data ''
    </pre>
    <p>Response</p>
    <pre>
    {
    "message": "Successful",
    "data": [
        {
            "email": "dr.lutf@objex.tech",
            "status": "SALES",
            "updated_at": "2023-09-01T11:51:29.189Z"
        },
        {
            "email": "hello@objex.tech",
            "status": "SALES",
            "updated_at": "2023-09-05T10:36:18.021Z"
        },
        {
            "email": "hellothere@unknowmdomain.com",
            "status": "NEW"
        }
        ...
    ]
}
    </pre>
    </details>
<details>
    <summary>Delete Lead</summary>
    <p>Request : </p>
    <pre>
curl --location --request DELETE 'https://api.nonprod.rabbito.io/crm' \
--header 'x-api-key: {{crm-x-api-key}}' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "hellothere@unknowndomain.com",
    "type": "lead",
    "source": "rabbito"
}'
    </pre>
    <p>Response</p>
    <pre>
    {
    "message": "Successful"
    }
    </pre>
    </details>

 <details>
    <summary>Sync users, CRM and Sendgrid </summary>
    <p>Request : </p>
    <pre>
curl --location --request POST 'https://api.nonprod.rabbito.io/crm/sync' \
--header 'x-api-key: {{crm-x-api-key}}' \
--data-raw '{
    "source": "rabbito"
}'
    </pre>
    <p>Response</p>
    <pre>
    {
    "message": "Syncing Successful"
}
    </pre>
    </details>

</details>

#

# Sendgrid-webhook

<details>
<summary>sendgrid-webhook</summary>
<p>
This service processes incoming SendGrid webhooks and integrates them with CRM system . It handles various SendGrid events, such as email opens, clicks, and bounces, and performs corresponding actions in the CRM, such as creating leads, updating lead information, or adding notes. 
</p>
<h5>
<h4>References:</h4>
<a>
https://console.cloud.google.com/functions/details/us-central1/sendgrid-webhook?env=gen2&project=rabbito&tab=source</a>
</details>
