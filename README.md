# Quill Forms Zapier API Docs

## Request:

### URL:

- Client website (bundle.authData.website_url)

### Method:

- POST

### Headers:

- content-type: application/x-www-form-urlencoded
- accept: application/json

### Body:

- Content type: application/x-www-form-urlencoded
- Must contains `api_key` parameter for authentication (bundle.authData.api_key)
- Must contains `action` parameter (See Actions Section below)

## Response:

### Status:

- 200 for success.
- 401 for unauthorized.
- 422 for unprocessable entity.
- other 4xx.

### Body:

- Content type: application/json
- json response contains:
  - `success`: boolean
  - `data`: array|object

## Actions:

### `test_authentication` :

Used to test the authentication (authentication.test).

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=test_authentication`

#### Success response example:

- status: 200
- body:

```
{
    success: true,
    body: {
        "message": "Successful authentication."
    }
}
```

#### Error response example:

- status: 401
- body:

```
{
    success: false,
    body: {
        "message": "Invalid api key."
    }
}
```

### `subscribe` :

Used for new form entry trigger subscription.

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=subscribe&form_id=1&zap_id=subscription:xxxxxxxx&zap_name=&hook_url=https://hooks.zapier.com/hooks/standard/xxxxxxxx/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx/`

### `unsubscribe` :

Used for cancelling new form entry trigger subscription.

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=unsubscribe&form_id=1&zap_id=subscription:xxxxxxxx`

### `get_forms` :

Used for polling available forms.

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=get_forms`

### `get_entries` :

Used for getting entry samples.

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=get_entries&form_id=1`

### `get_fields` :

Used for getting form fields.

#### Request example:

- POST {bundle.authData.website_url}
- headers  
  `content-type: application/x-www-form-urlencoded`  
  `accept: application/json`
- body:  
  `api_key={bundle.authData.api_key}&action=get_fields&form_id=1`
