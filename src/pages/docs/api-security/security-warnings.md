The following list describes possible warning messages and potential ways to resolve them.

* [Global security field should properly enforce security](#global-security-field-should-properly-enforce-security)

    * [Security field is not defined](#security-field-is-not-defined)
    * [Security field does not contain any item](#security-field-does-not-contain-any-item)
    * [Security field does not contain any scheme](#security-field-does-not-contain-any-scheme)
    * [Scope for OAuth scheme used in security field not defined in the securityScheme declaration](#scope-for-oauth-scheme-used-in-security-field-not-defined-in-the-securityscheme-declaration)
* [Reusable security schemes are not defined within components](#reusable-security-schemes-are-not-defined-within-components)
    * [Security scheme object not defined](#security-scheme-object-not-defined)
* [Security field for an individual operation should properly enforce security](#security-field-for-an-individual-operation-should-properly-enforce-security)
    * [Security field for the operation does not contain any item](#security-field-for-the-operation-does-not-contain-any-item)
    * [Security field for the operation does not contain any scheme](#security-field-for-the-operation-does-not-contain-any-scheme)
    * [Operation does not enforce any security scheme](#operation-does-not-enforce-any-security-scheme)
    * [Scope for OAuth scheme used not defined in the securityScheme declaration](#scope-for-oauth-scheme-used-not-defined-in-the-securityscheme-declaration)
* [Security field for an individual operation should properly enforce security](#security-field-for-an-individual-operation-should-properly-enforce-security)
    * [API accepts credentials from OAuth authentication in plain text](#api-accepts-credentials-from-oauth-authentication-in-plain-text)
    * [API accepts auth credentials in plain text](#api-accepts-auth-credentials-in-plain-text)
    * [Global server URL uses HTTP protocol](#global-server-url-uses-http-protocol)
    * [API accepts credentials from OpenID Connect authentication in plain text](#api-accepts-credentials-from-openid-connect-authentication-in-plain-text)
* [Server configuration of the operation allows insecure enforcement of security schemes](#server-configuration-of-the-operation-allows-insecure-enforcement-of-security-schemes)
    * [Operation accepts credentials from OAuth authentication in plain text](#operation-accepts-credentials-from-oauth-authentication-in-plain-text)
    * [Operation accepts authentication credentials in plain text](#operation-accepts-authentication-credentials-in-plain-text)
    * [Server URL of the operation is using HTTP protocol](#server-url-of-the-operation-is-using-http-protocol)
    * [Operation accepts credentials from OpenID Connect authentication as plain text](#operation-accepts-credentials-from-openid-connect-authentication-as-plain-text)
* [Security scheme configuration allows loopholes for credential leaks](#security-scheme-configuration-allows-loopholes-for-credential-leaks)
    * [Authorization URL uses HTTP protocol. Credentials will be transferred as plain text](#authorization-url-uses-http-protocol-credentials-will-be-transferred-as-plain-text)
    * [Token URL uses HTTP protocol](#token-url-uses-http-protocol)

## Global security field should properly enforce security

### Security field is not defined

| Severity | Issue description | Possible fix |
| -------- | ----------------- | ------------ |
| High | If the global security field is not defined, the API does not require any authentication by default. Anyone can access the API operations that do not have a security field defined. | The security field should be defined in the schema. |

**Resolution:**

```yaml
openapi: 3.0.0
info:
paths:
security:
    - testAuth : []
```
### Security field does not contain any item

| Severity | Issue description | Possible fix |
| -------- | ----------------- | ------------ |
| High | If the security field contains an empty array, no security scheme is applied to the operations by default. | The security field should contain at least one item in the array. |

**Resolution:**

```yaml
openapi: 3.0.0
info:
paths:
security:
    - testAuth : []
```

### Security field does not contain any scheme

| Severity | Issue description | Possible fix |
| -------- | ----------------- | ------------ |
| High | An empty object in the security field disables the authentication completely. Without security fields defined for each operation, anyone can access the API operations without any authentication. | Security field array items should not contain an empty object. |

**Resolution:**

```yaml
openapi: 3.0.0
info:
paths:
security:
    - testAuth : []
```

### Scope for OAuth scheme used in security field not defined in the securityScheme declaration

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Low | The OAuth2 scopes used in the global security field should be defined in the security schemes field. Otherwise, an attacker can introduce their scopes to fill the gap and exploit the system. | Make sure that all the OAuth2 scopes used are defined in the the OAuth2 security scheme. |

**Resolution:**

```yaml
security:
  - OAuth2:
    - read
    - write
components:
  securitySchemes:
    OAuth2:
      type: oauth2
      flows:
        authorizationCode:
          scopes:
            read: read objects in your account
            write: write objects to your account
```

## Reusable security schemes are not defined within components

### Security scheme object not defined

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| High | The components object of the API does not declare any security schemes which can be used in the security field of the API or individual operations. | Security schemes should be defined in the schema of the component. |

**Resolution:**

```yaml
components:
  securitySchemes:
    testAuth:
      type: http
      scheme: basic
```

## Security field for an individual operation should properly enforce security
### Security field for the operation does not contain any item

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | No security scheme is applied to the API operation by default. | The security field in any operation should contain at least one item in the array. |

**Resolution:**

```yaml
paths:
  /user:
    get:
      security:
      - testAuth : []
```

### Security field for the operation does not contain any scheme

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | An empty object in the security field disables the authentication completely for the operation. Anyone can access the API operation without any authentication. | Specify at least one security requirement in the operation. |

**Resolution:**

```yaml
paths:
  /user:
    get:
      security:
      - testAuth : []
```

### Operation does not enforce any security scheme

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium |  If both the global security field and operation’s security field are not defined, anyone can access the API without any authentication. | Define a security field in the operation. |

**Resolution:**

```yaml
  /user:
    get:
      tags:
      response:
      security:
          - testAuth : []
```

### Scope for OAuth scheme used not defined in the securityScheme declaration

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Low | The OAuth2 scopes used in the  security field of the operation should be defined in the security schemes field. Otherwise, an attacker can introduce their scopes to fill the gap and exploit the system. | Make sure that all the OAuth2 scopes used are defined in the the OAuth2 security scheme. |

**Resolution:**

```yaml
paths:
  "/user":
    get:
      summary: 'Sample endpoint: Returns details about a particular user'
      operationId: listUser
      security:
      - OAuth2:
        - read
        - write
components:
  securitySchemes:
    OAuth2:
      type: oauth2
      flows:
        authorizationCode:
          scopes:
            read: read objects in your account
            write: write objects to your account
```

## Global server configuration allows insecure enforcement of security schemes

### API accepts credentials from OAuth authentication in plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| High | The access tokens are sent as plain text over an unencrypted network. Attackers can intercept the access tokens simply by listening to the network traffic in a public Wi-Fi network. | Make sure that the server URL is a valid URL and uses HTTPS protocol. |

**Resolution:**

```yaml
servers:
  - url: https://my.api.example.com/
    description: API server
# ...  
components:
  securitySchemes:
    OAuth2:
      type: oauth2
# ...
security:
  - OAuth2:
      - write
      - read
```

### API accepts auth credentials in plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| High | The credentials are sent as plain text over an unencrypted network. Attackers can intercept the credentials simply by listening to the network traffic in a public Wi-Fi network. | Make sure that the server URL is a valid URL and uses HTTPS protocol. |

**Resolution:**

```yaml
servers:
  - url: https://my.api.example.com/
    description: API server
# ...
components:
  securitySchemes:
    apiAuth:
      type: http
      scheme: api
# ...  
security:
  - apiAuth: []
```

### Server URL uses HTTP protocol

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The server supports unencrypted HTTP connections, all requests and responses will be transmitted in the open. Anyone listening to the network traffic while the calls are being made can intercept them. | Make sure the URL uses HTTPS protocol. |

**Resolution:**

```yaml
servers:
  - url: https://my.api.server.com/
    description: API server
# ...
components:
  securitySchemes:
    OAuth2:
      type: oauth2
# ...
security:
  - OAuth2:
      - write
      - read
```

### API accepts credentials from OpenID Connect authentication in plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The credentials are sent as plain text over an unencrypted network. Attackers can intercept the access tokens simply by listening to the network traffic in a public Wi-Fi network. | Make sure the server URL follows HTTPS protocol. |

**Resolution**:

```yaml
servers:
  - url: https://my.api.server.com/
    description: API server
# ...  
components:
  securitySchemes:
    OpenIdScheme:
      type: openIdConnect
# ...
security:
  - OAuth2:
      - write
      - read
```

## Operations server configuration allows insecure enforcement of security schemes

### Operation accepts credentials from OAuth authentication in plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The API operation accepts the access tokens from a flow that are transported in plain text over an unencrypted channel. Attackers can easily intercept API calls and retrieve the unencrypted tokens. They can then use the tokens to make other API calls. | Make sure that the server URL is a valid URL and follows HTTPS protocol. |

**Resolution:**

```yaml
components:
  securitySchemes:
    OAuth2:
      type: oauth2
paths:
  "/pets":
    post:
      operationId: addPet
      servers:
      - url: https://my.api.server.com/
        description: API server
```

### Operation accepts authentication credentials in plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The API operation accepts the credentials that are transported in plain text over an unencrypted channel. Attackers can easily intercept API calls and retrieve the unencrypted tokens. They can then use the tokens to make other API calls. | Make sure that the server URL is a valid URL and follows HTTPS protocol. |

**Resolution:**

```yaml
components:
  securitySchemes:
    ApikeyAuth:
      type: apiKey
paths:
  "/pets":
    post:
      operationId: addPet
      servers:
      - url: https://my.api.server.com/
        description: API server
```

### Server URL is using HTTP protocol

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The API operation supports unencrypted HTTP connections, all requests and responses will be transmitted in the open. Anyone listening to the network traffic while the calls are being made can intercept them. | Make sure that the URL uses HTTPS protocol. |

**Resolution:**

```yaml
get:
  operationId: getPetsById
  servers:
    - url: https://test.api.com
```

### Operation accepts credentials from OpenID Connect authentication as plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The credentials for an operation are sent as plain text over an unencrypted network. Attackers can intercept the access tokens simply by listening to the network traffic in a public Wi-Fi network. | Make sure server field of the operation follows HTTPS protocol. |

**Resolution**:

```yaml
components:
  securitySchemes:
    OpenIdScheme:
      type: openIdConnect
      openIdConnectUrl: https://my.api.server.com/
paths:
  "/pets":
    post:
      operationId: addPet
      servers:
      - url: https://my.api.server.com/
        description: API server
```

## Global server configuration allows insecure enforcement of security schemes

### Authorization URL uses http protocol. Credentials will be transferred as plain text

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | The server accepts the credentials over an unencrypted network. Anyone listening to the network traffic while the calls are being made can intercept them. | Make sure that the authorization URL is a valid URL and follows HTTPS protocol. |

**Resolution:**

```yaml
type: oauth2
flows:
  implicit:
    authorizationUrl: https://test.com
```

### Token URL uses HTTP protocol

| Severity | Issue description | Possible fix |
| ----------- | ----------- | ----------- |
| Medium | Tokens are transported over an unencrypted channel. Anyone listening to the network traffic while the token is being sent can intercept it. | Make sure that the token URL is a valid URL and follows HTTPS protocol. |

**Resolution:**

```yaml
type: oauth2
flows:
  implicit:
    tokenUrl: https://test.com
```
