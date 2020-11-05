---
description: This article provides an overview of making API calls to Upsolver.
---

# Upsolver REST API

For API calls to Upsolver, you will need a token. When you generate this API token, save the token somewhere safe as you will not be able to retrieve it again. 

You can create an API token in the Upsolver UI or using a POST request.

{% hint style="info" %}
The **API Tokens** page can be found by clicking **More &gt; API Tokens**.
{% endhint %}

## Create an API token

1. From the **API Tokens** page, click **Generate**.

2. **Name** this API token.

3. Click **Generate**.

4. Either **download** or **copy** the token.

{% hint style="danger" %}
After closing this window, you will **not** be able to retrieve the full API token.

**Save it somewhere safe.**
{% endhint %}

5. Click **Close**.

## Create an API Token using a POST request

You can send a POST request to `/api-tokens` with the name and description of your API token and your email and password in the headers; this will return an API token. 

{% hint style="warning" %}
Save the token somewhere safe as you will not be able to retrieve this token again.
{% endhint %}

#### Example request:

```bash
curl --request POST \
--url https://api.upsolver.com/api-tokens/ \
--header 'content-type: application/json' \
--header 'x-api-email: YOUR_EMAIL_HERE' \
--header 'x-api-password: YOUR_PASSWORD_HERE' \
--data '{
	"displayData": {
		"name": "Data Sources Bot API Token",
		"description": "API Token used by the bot 
to create Data Sources"
	}
}'
```

#### Example response:

```http
{
	"id": "12345678-1234-1234-1234-1234567890ab",
	"organizationId": "12345678-1234-1234-1234-1234567890ab",
	"displayData": {
		"name": "Data Sources Bot API Token",
		"description": "API Token used by the bot 
to create Data Sources",
		"statusMessage": "ok",
		"statusType": "ok",
		"creationTime": "2018-11-01T12:09:27.971Z",
		"createdBy": "Documentation Bot 
(docs@upsolver.com)"
	},
	"apiToken": "abc12345678901234567890123456789",
	"createdBy": "docs@upsolver.com"
}
```

## Using the API token

Include the token in the API request `authorization` header.

#### Example use:

```bash
curl --request GET 
 --url https://api.upsolver.com/inputs/
 --header 'authorization: API_TOKEN'
```

## Delete an API token

1. Navigate to the **API Tokens** page found under **More &gt; API Tokens**.

2. Click the trash icon![](../../.gitbook/assets/image%20%282%29.png)next to the token to delete.

