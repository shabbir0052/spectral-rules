#### Overview
Spectral is an Open-Source API Style Guide Enforcer / Linter to make api consistance and secure

##### Setting up spectral locally 

Change to the directory where open API spec resides

Install the following npm modules

`npm install -g @stoplight/spectral-cli`


Install the style guide

`npm install --save -D @stoplight/spectral-owasp-ruleset`

`npm install --save -D spectral-aws-apigateway-ruleset`


Copy .spectral.yaml, from this repository  to the local folder

Run the rules  
   `spectral lint api/openapi.yaml`


You will see the following response. Ensure that warning and errors are resolved as much as possible before checking in the API spec to git hub/API portal
```dos
  46:7       warning  api-health                                Creating a `/health` endpoint is a simple solution for pull-based monitoring and manually checking the status of an API.      paths
  46:7       warning  api-home                                  Stop forcing all API consumers to visit documentation for basic interactions when the API could do that itself.               paths
  47:27      warning  paths-kebab-case                          /adjusterDetails/health should be kebab-case (lower case and separated with hyphens).                                         paths./adjusterDetails/health
  48:9   information  owasp:api2:2019-protection-global-safe    This operation is not protected by any security scheme.                                                                       paths./adjusterDetails/health.get
  52:17      warning  owasp:api3:2019-define-error-validation   Missing error validation response of either 400 or 422.                                                                       paths./adjusterDetails/health.get.responses
  52:17      warning  owasp:api4:2019-rate-limit-responses-429:429 response should be defined.. Missing responses[429]                                                                       paths./adjusterDetails/health.get.responses
  53:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails/health.get.responses[200]
  62:35        error  adv-security-schemes-defined              This API definition does not have any security scheme defined.                                                                paths./adjusterDetails/health.get.responses[200].content.application/json.examples['Health Response'].value.components
  74:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails/health.get.responses[401]
  77:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails/health.get.responses[401].content.application/json
  85:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails/health.get.responses[500].content.application/json
  90:28        error  adv-security-schemes-defined              This API definition does not have any security scheme defined.                                                                paths./adjusterDetails/health.get.responses[500].content.application/json.example.components
  99:20      warning  paths-kebab-case                          /adjusterDetails should be kebab-case (lower case and separated with hyphens).                                                paths./adjusterDetails
  100:9  information  owasp:api2:2019-protection-global-safe    This operation is not protected by any security scheme.                                                                       paths./adjusterDetails.get
 105:17        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./adjusterDetails.get.parameters[0].name
 114:17        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./adjusterDetails.get.parameters[1].name
 134:17      warning  owasp:api4:2019-rate-limit-responses-429:429 response should be defined.. Missing responses[429]                                                                       paths./adjusterDetails.get.responses
 135:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails.get.responses[200]
 186:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails.get.responses[400]
 189:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails.get.responses[400].content.application/json
 198:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails.get.responses[401]
 201:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails.get.responses[401].content.application/json
 206:15        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./adjusterDetails.get.responses[404]
 209:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails.get.responses[404].content.application/json
 217:30      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./adjusterDetails.get.responses[500].content.application/json
 223:13  information  owasp:api2:2019-protection-global-safe    This operation is not protected by any security scheme.                                                                       paths./api/v2/claims/adjuster/supervisors.get
 227:25        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./api/v2/claims/adjuster/supervisors.get.parameters[0].name
 241:25        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./api/v2/claims/adjuster/supervisors.get.parameters[2].name
 254:23      warning  owasp:api3:2019-define-error-validation   Missing error validation response of either 400 or 422.                                                                       paths./api/v2/claims/adjuster/supervisors.get.responses
 254:23      warning  owasp:api4:2019-rate-limit-responses-429:429 response should be defined.. Missing responses[429]                                                                       paths./api/v2/claims/adjuster/supervisors.get.responses
 256:29        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[200].headers
 257:46        error  no-x-response-headers                     Headers cannot start with X-, so please find a new name for X-ApplicationContext. More: https://tools.ietf.org/html/rfc6648.  paths./api/v2/claims/adjuster/supervisors.get.responses[200].headers.X-ApplicationContext
 277:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[400]
 279:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[400].content.application/json
 283:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[401]
 285:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[401].content.application/json
 289:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[403]
 291:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[403].content.application/json
 295:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[409]
 297:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[409].content.application/json
 301:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisors.get.responses[422]
 303:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[422].content.application/json
 309:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisors.get.responses[500].content.application/json
 320:13  information  owasp:api2:2019-protection-global-safe    This operation is not protected by any security scheme.                                                                       paths./api/v2/claims/adjuster/supervisor/health.get
 324:25        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./api/v2/claims/adjuster/supervisor/health.get.parameters[0].name
 331:25        error  no-x-headers                              Headers cannot start with X-, so please find a new name for name. More: https://tools.ietf.org/html/rfc6648.                  paths./api/v2/claims/adjuster/supervisor/health.get.parameters[1].name
 337:23      warning  owasp:api4:2019-rate-limit-responses-429:429 response should be defined.. Missing responses[429]                                                                       paths./api/v2/claims/adjuster/supervisor/health.get.responses
 339:29        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisor/health.get.responses[200].headers
 346:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisor/health.get.responses[400]
 348:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisor/health.get.responses[400].content.application/json
 352:23        error  owasp:api4:2019-rate-limit                All 2XX and 4XX responses should define rate limiting headers.                                                                paths./api/v2/claims/adjuster/supervisor/health.get.responses[401]
 354:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisor/health.get.responses[401].content.application/json
 360:42      warning  no-unknown-error-format                   Every error response SHOULD support either RFC 7807 (https://tools.ietf.org/html/rfc7807) or the JSON:API Error format.       paths./api/v2/claims/adjuster/supervisor/health.get.responses[500].content.application/json
 366:12        error  adv-security-schemes-defined              This API definition does not have any security scheme defined.                                                                components        
 440:20        error  adv-security-schemes-defined              This API definition does not have any security scheme defined.                                                                components.schemas.HealthResponse.properties.components`
```
 

##### References

 - Some popular style guide can be found here
    https://github.com/stoplightio/spectral-rulesets
  - Getting started
    https://docs.stoplight.io/docs/spectral/674b27b261c3c-overview

 