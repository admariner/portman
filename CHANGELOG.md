## [Unreleased]

## v1.32.1 - (2025-07-10)

- Fuzzing - only map required fields if required property is an array (#702)
- Contract testing - Handle default response code (#431)
- Variation testing - Handle default response code (#431)
- Variations - Support wildcard for response codes

## v1.32.0 - (2025-07-09)

- Variations - Set content-type for response
- Variations - Set content-type for request body
- Contract testing - Set content-type for request body
- Contract testing - Set content-type for response
- Added examples for variation & contract testing with multiple content-types
- Overwrites - Added support for overwriting file form-data values
- Bumped dependencies openapi-format 1.27.1

## v1.31.1 - (2025-04-03)

- Removed Clearbit references (#693)
- Bumped dependencies openapi-format 1.25.2

## v1.31.0 - (2025-03-29)

- Bumped openapi-to-postman to 5.0.0

## v1.30.8 - (2025-03-29)

- Generate safe variable names in the Postman scripts (#687)
- CLI - Warn about unsupported flags (#686)
- Bumped dependencies: openapi-format 1.25.1

## v1.30.7 - (2024-11-05)

- matchPath - Improved matching with ending wildcard (#674)

## v1.30.6 - (2024-11-01)

- matchPath - Further improved path matching (#672)

## v1.30.5 - (2024-11-01)

- Apply casing to auth variable (#668)
- Improved path matching (#669)
- Improved documentation(#671)
- Warn for missing targets (#632 #391)

## v1.30.4 - (2024-10-07)

- Handle Postman API non-200 responses better (#660)
- Handle scalar $ref: >- (#661)

## v1.30.3 - (2024-09-27)

- Improved loading split local OpenAPI files
- Bumped dependencies: openapi-format 1.24.0

## v1.30.2 - (2024-09-11)

- testResponseBodyContent - prevent PM variables as string (#650)
- testResponseHeaderContent - support using PM variables in oneOf check
- overwrite - handle overwrite of non-empty objects with plain values (#646)
- Bumped dependencies: openapi-format 1.23.0

## v1.30.1 - (2024-08-27)

- Improved OpenAPI to JSON schema conversion to handle OpenAPI-specific properties (#642 #494)
- Strip unneeded OpenAPI-specific properties ('discriminator', 'readOnly', 'writeOnly', 'xml', 'externalDocs', 'example','deprecated') for more compact JSON schemas.
- Added JSON schema validation warning during conversion, to inform the users. (#644)
- Fix for unwanted minItems, maxItems addition in the JSON schema
- overwriteRequestQueryParams - Remove form encoded array query params ((#640))
- overwriteRequestQueryParams - Insert additional form encoded array query params (#640)
- Bumped dependencies: newman

## v1.30.0 - (2024-08-23)

- Portman - sort Postman folders based on the "orderOfFolders" configuration (#621)
- overwriteRequestQueryParams - Handle form encoded array query params (#640)

## v1.29.3 - (2024-08-19)

- Portman - Make OpenAPI data immutable (#630)
- Bumped dependency openapi-format
- Removed unused yaml package 

## v1.29.2 - (2024-08-19)

- Skip read-only properties from request body (#628)
- YAML error fix using latest openapi-format (#631)
- Bumped dependencies: openapi-to-postman 4.24.0, newman, openapi-format

## v1.29.1 - (2024-08-08)

- Fuzzing - Handle nested plain array values (#629)

## v1.29.0 - (2024-08-06)

> [!IMPORTANT]  
> **Important Change:** If you are using version 1.28.0 with a custom Postman config file specified by the `--postmanConfigFile` flag, please ensure that the `parametersResolution` option is set to either "Example" or "Schema". The options `requestParametersResolution` and `exampleParametersResolution` are deprecated openapi-to-postman options.

- Conversion - Use convertV2 from openapi-to-postman
- overwriteRequestSecurity - handle missing auth (#622)
- Fuzzing - Fix nested path handling (#624)
- Globals - Strip response example from root requests

## v1.28.0 - (2024-07-22)

- overwriteRequestQueryParams - Added wildcard matching for query param keys (#612)
- OpenAPI conversion - Use the first-listed content-type as request body (#601)
- overwriteRequestSecurity - Improved logic to handle OAuth2
- overwriteRequestHeaders - Fix missing request auth (#600)
- assignVarFromValue - Add template expressions as value (#595)
- Template expression: Fix to handle double/triple curly braces (#597)
- overwriteRequestHeaders - Allow zero value
- overwriteRequestPathVariables - Allow zero value
- overwriteRequestQueryParams - Allow zero value (#603)
- Fuzzing - Improve fuzzing with zero values (#599)
- Improved OpenAPI parsing error reporting (#591)
- Dependencies - Replaced faker with @faker-js (#593)
- Updated overwrite examples and added preRequestScripts example by @jpjpjp (#598)
- Bumped dependencies: openapi-to-postman 4.23.0, replaced traverse with neotraverse, removed camelCase

## v1.27.0 - (2024-06-16)

- overwrites - Added the removal of Authorization using overwriteRequestHeaders,overwriteRequestSecurity, securityOverwrites (#580)
- Improved OpenAPI version to Postman version conversion (#578)
- Updated readme & examples by @jpjpjp 
- Bumped dependencies

## v1.26.6 - (2024-06-05)

- Add OpenAPI version conversion to Postman Collection version (handy for usage in Microcks) (#577)
- Bumped dependencies: openapi-to-postman 4.21.0

## v1.26.5 - (2024-03-08)

- headersPresent: Add check only for required headers (#566)

## v1.26.4 - (2024-03-06)

- Bugfix to support http & https remote files (#562)

## v1.26.3 - (2024-02-07)

- overwriteRequestQueryParams - Auto-enable query parameters when overwrite value is set (#559)
- overwriteRequestHeaders - Auto-enable headers when overwrite value is set (#559)
- normalizedPathRef: Improve handling colon character (#556)

## v1.26.2 - (2024-01-28)

- Fuzzing - Enable query parameters and headers for fuzzed values (#554)

## v1.26.1 - (2024-01-18)

- overwriteRequestHeaders: Added disable false option (#551)
- Bumped dependencies: openapi-to-postman 4.19.0 (#551)

## v1.26.0 - (2024-01-16)

- Portman - Change default enableOptionalParameters setting to false (#550)

> [!CAUTION]  
> **Breaking Change:** The default behaviour of the Query parameters is changed since version 1.26.0.<br>Optional query parameters will be disabled in Postman by default.

This will reduce the need for extra Portman config to disable the optional query parameters in the Postman collection and provide a more expected result in Postman.

OpenAPI:
```yaml
    limitParam:
      name: limit
      in: query
      description: (Required) Number of records to return
      required: true # <----------
      schema:
        type: string
```

**BEFORE**

All the query parameters are enabled in the Postman collection.

<img src="./examples/postman-to-k6/images/enable-optional-parameters-before.png" width="1021" >

**AFTER**

Only the required query parameters are enabled in the Postman collection.

<img src="./examples/postman-to-k6/images/enable-optional-parameters-after.png" width="1018" >

You can modify this default behaviour by using `--postmanConfigFile` parameters.
This will allow you to provide a specific configuration file that will be used for converting the OpenAPI specification to Postman.

See [postmanConfigFile](https://github.com/apideck-libraries/portman?tab=readme-ov-file#pass-custom-paths-for-config-files) example for more info.

## v1.25.1 - (2024-01-16)

- AssignVariables: Fix casing for template expressions for variable props (#549)

## v1.25.0 - (2024-01-15)

- AssignVariables: Option to use template expressions for variable names (#548)
- AssignVariables: Option to use template expressions for variable properties for Request body, Response body & header (#548)
- Overwrites: Option to use template expressions for values (#548)
- Globals: Define the casing of the generated variable names (#541)
- Globals: Apply variableCasing for injected .ENV variables (#548)
- Globals: Define the separatorSymbol used in the Postman test names (#541)
- Support for loading local or remote JSON/YAML config files (#547)
- Implement openapi-format as module (#539)
- Fix includeTests parameter behaviour (#544)
- Updated examples

## v1.24.0 - (2024-01-05)

- Globals - Added the option set 'collectionVariables' for setting variables on collection level

## v1.23.2 - (2024-01-05)

- Added $schema to the Portman JSON Schema for auto-completion
- Bumped dependencies: openapi-to-postmanv2 4.18.0, newman 6.1.0, postman-collection 4.3.0, openapi-format 1.15.2, axios 1.6.4

## v1.23.1 - (2023-10-28)

- overwriteRequestSecurity - Handle missing auth config (#509)
- overwriteRequestQueryParams - Enable disabled query params (#484)

## v1.23.0 - (2023-10-28)

- orderOfOperations - Adjusted ordering string matching to be exact when wildcard is not present (#490)
- ContentTests - Add pm variable support for oneOf assertions in content tests (#520)
- Postman Sync - Set no limit to the body size on collection update (#517)
- Postman Sync - Removes extra query params from url for the file name (#525)
- Fuzzing - Exclude properties with reserved names from fuzzing (#514)
- Bugfix for overwriteRequestBody - should root overwrite (#524)
- Bumped dependencies

## v1.22.0 - (2023-03-26)

- syncPostmanCollectionIds - Synchronises the IDs of newly created postman collections (#457)
- securityOverwrites - Set auth settings when no auth is defined (#472)
- overwriteRequestSecurity - Keep API key when no key is provided (#468)
- orderOfOperations - Prevent error (#467)

## v1.21.0 - (2023-02-27)

- Bumped openapi-to-postman to 4.9.0 which support OpenAPI 3.1
- Bugfix for integrationTests - merge folders/suites into one (#361)
- Bugfix to overwrite request headers with empty values (#459)
- Bugfix for overwriteRequestBaseUrl - overwrite value with path parameters excludes parameters (#446)
- Bugfix for handling Postman variables in the path when targeting (#445)
- Bugfix for handling null values safer for analyzeFuzzJsonSchema (#443)
- Bugfix for handling variable injection of the baseUrl & server variables (#408, #437)
- Bumped dependencies

## v1.20.1 - (2022-12-06)

- Bugfix "overwriteRequestBaseUrl" to keep the path parameters (#434)

## v1.20.0 - (2022-12-06)

- AssignVariables - Added support to assign the root of the request body as variable (#429)
- Overwrites - added "overwriteRequestBaseUrl" to overwrite the request base url
- Bumped dependencies

## v1.19.0 - (2022-11-06)

- overwriteRequestBody - added support for type "form-data" (#325)
- overwriteRequestBody - added support for type "x-www-form-urlencoded" (#325)
- AssignVariables - Added support for null values for response body (#414)
- ContentTests - Added support for null values for response body (#414)
- ContentTests - Added support to look up a key within an array of objects by using a * wildcard (#417)
- Documentation - Updated the ordering example (#418,#423)
- Added Portman as Docker (#260)

## v1.18.1 - (2022-09-30)

- Fix unwanted schema validation (#392)
- Fix Newman option not properly formatted (#395)
- Bumped dependencies

## v1.18.0 - (2022-07-19)

- Overwrites - Automatically convert values for request query parameters, path variables & headers to string (#336, #384)
- Fix ContentTests with length/minLength/maxLength checks with 0 (zero) as value (#369)
- Fix ContentTests with empty as value
- ContentTests - Added "notExist" check for response body & headers (#364)
- ContentTests - Added "assert" option for response body & headers (#372)
- ContentTests - Added support for special characters in request body property names (#365)
- AssignVariables - Added support for special characters in request body property names (#365)
- Postman Sync - Fix for issue where POSTMAN_COLLECTION_UID was ignored (#353)
- Postman Sync - Improved the Portman API output for API error. (#367)
- overwriteRequestPathVariables - Support empty as value (#382)
- overwriteRequestPathVariables - Added the option to insert new path variables in Postman
- overwriteRequestPathVariables - Added the option to remove path variables in Postman
- Bumped dependencies

## v1.17.0 - (2022-06-21)

- Fix missing integrationTests when using "bundleContractTests" (#330)
- ContentTests - allow targeting of root object or array (#334)
- Tests - support bracket notation for targeted keys (#333)
- Fuzzing - support JSON variants as content-type (#332)
- Fuzzing - added support for allOf, anyOf, oneOf schemas (#335)
- Fuzzing - added min/maxLength support for arrays (#335)
- ContentTest - Added "oneOf" check for response body & header (#313)
- Bumped dependencies openapi-format, jest, @apideck/better-ajv-errors, @apidevtools/swagger-parser, fs-extra

## v1.16.1 - (2022-04-13)
- Set the 'logAssignVariables' option via 'cliOptions' to toggle console output for assigned variables

## v1.16.0 - (2022-04-13)
- Bumped dependency versions of ajv, yargs, fp-ts
- Added the 'logAssignVariables' CLI option to toggle console output for assigned variables (#317)
- Globals - Added the option set 'collectionTestScripts' for Test Scripts on collection level (#305)
- Globals - Overwrite OpenAPI authorization with the 'securityOverwrites' (#306)

## v1.15.1 - (2022-04-01)
- ExtendTest - Allow importing files for extendTest (#304)
- Extended supported OpenAPI methods (#306)
- Fix for incorrect en/decoding of boolean/number Postman variables (#286)
- Enhance generated schema validation to support double as a format (#307)

## v1.15.0 - (2022-03-28)
- Bumped dependency versions of axios, ajv, @apideck/better-ajv-errors, Newman, and openapi-format
- Enhance generated schema validation to support float as a format (#281)
- Fix handling of the Global configuration properties (#261) 
- Improved file handling, including support for directory creation (#278)
- Support $ref for Portman config (#277)
- Set Postman variables as boolean & number types in overwriteRequestBody (#295)
- securityOverwrites - Added support for Postman authorization options (#272)

## v1.14.2 - (2022-02-22)

- Fuzzing - skip nullable required properties
- Bumped dependency follow-redirects

## v1.14.1 - (2022-02-10)

- Bumped dependencies openapi-format to 1.9.2

## v1.14.0 - (2022-02-09)

- Allow importing files for operationPreRequestScripts and collectionPreRequestScripts
- Contract test - extended "jsonBody" to verify that a 204 response has no response body content
- Bumped dependencies openapi-format to 1.9.1
- Bumped dependencies openapi-to-postman to 2.14.1

REMARK: openapi-to-postman v2.14.1 introduces the change that the "Accept" header is now set based on the response content-type by default. For more info visit the [Github PR](https://github.com/postmanlabs/openapi-to-postman/pull/459).
Additionally [disableBodyPruning](https://github.com/postmanlabs/openapi-to-postman/issues/467), a Postman specific property is added to the generated request object.

## v1.13.1 - (2022-01-17)

- Extended orderOfOperations to include the sorting on root level, next to the folder sorting (#236)
- Fix for status code in contract test (#238)
- Patch for follow-redirects vulnerability
- Bumped dependencies

## v1.13.0 - (2021-12-15)

- Contract test - extend JSON schema validation with option to set additional properties behaviour.
- ContentTest - Check length of array or string
- ContentTest - Check minimum length of array or string of response body
- ContentTest - Check maximum length of array or string of response body
- ContentTest - Check minimum length of array or string of response header
- ContentTest - Check maximum length of array or string of response header
- Fix for orderOfOperations for operations have multiple path variables (#208)
- Implemented suggested fix for orderOfOperations with * wildcard (#122)
- Updated dependencies

## v1.12.2 - (2021-12-15)

- Added better handling of Postman API errors

## v1.12.1 - (2021-12-03)

- Fuzzing - added support for deeply nested required properties in the request body
- Bugfix for unwanted removal of operations without OperationId when using "excludeForOperations" (#185)
- Bumped openapi-format to version 1.7.0

## v1.12.0 - (2021-12-01)

- Added `--ignoreCircularRefs` option to allow OAS specs that contain invalid circular references to still be processed by Portman
- Added the `--collectionName` option to change the OpenAPI title & Postman collection name
- Added `--stripResponseExamples` CLI option to slim down generated Postman collection
- Fuzzing - added support for root array structure in the request body
- Update package dependencies

## v1.11.0 - (2021-11-30)

- Improved caching of Postman API, reducing API calls towards Postman
- Added "postmanFastSync" option to sync collections faster by using delete & create of a new collection (new UID), instead of an update
- Added "postmanRefreshCache" Postman sync option to refresh all local cached Postman API data
- Added Fuzzing support for deeply nested properties

## v1.10.2 - (2021-11-29)

- Support Node 12 (#175)

## v1.10.1 - (2021-11-22)

- Fixed missing collection name issue (#171)
- Improved formatting of variation test example config (#170)

## v1.10.0 - (2021-11-15)

- Overwrites - Extended the overwriteRequestHeaders capabilities with the option to insert new headers in Postman
- Overwrites - Extended the overwriteRequestQueryParams capabilities with the option to insert new query params in Postman
- ContentTest - Added new test type "requestHeader"
- ContentTest - Extended the ContentTest for "requestBody" with checks : contains, length
- ContentTest - Added the ContentTest for "requestHeader" with checks : key, value, contains, length
- Variation Testing - Added the option to target the expected openApiResponse, skipping the variation if the response is not defined in OpenAPI
- Added support for loading cliOptionsFile in YAML format
- Fix for bundle contract folder issue (#145)
- Rework PostmanSyncService to be more resilient when handling cross workspace workflows (#164)
- Extend unit tests for Postman class itself
- Update Portman Config jsonSchema
- Fix typo in OAS URL error string (#168)
- Fuzzing - Added fuzzing variation generation of the request body fields for OpenAPI properties: required, minimum number, maximum number, minLength, maxLength
- Fuzzing - Added fuzzing variation generation of the request query parameters for OpenAPI properties: required, minimum number, maximum number, minLength, maxLength
- Fuzzing - Added fuzzing variation generation of the request headers for OpenAPI properties: required, minimum number, maximum number, minLength, maxLength
- Fuzzing - Added support for Postman Dynamic Variables on the minLength, maxLength for fuzzing options

## v1.9.3 - (2021-10-20)

- Improved the handling of JSON schema maxItems/minItems for the types: array or null
- Bumped dependencies

## v1.9.2 - (2021-10-12)

- Added support for passing postmanWorkspaceName & postmanUid as .ENV variables
- Improved the "raw replacements" method to handle the special characters safely
- Bumped dependencies

## v1.9.1 - (2021-10-04)

- Support loading Portman config in YAML format
- Added `newmanOptionsFile` as a Portman CLI option, to pass options for configuring Newman
- Bumped dependencies

## v1.9.0 - (2021-09-30)

- Due to a quirk, 1.9.0 was a ghost. All changes are released in 1.9.1.

## v1.8.3 - (2021-09-27)

- Support overwrites for a request body array and array related cases (#143)
- Implemented optional chaining for safer handling of JSON response when assigning vars
- Added an INFO message when variable could not be assigned

## v1.8.2 - (2021-09-17)

- Code rebuild of missing fix for unwanted maxItems (#133)
- Handle array for assign responseBodyProp (#134)
- Documented "operationPreRequestScripts" properties in the readme

## v1.8.1 - (2021-09-02)

- Bug fix for unwanted maxItems on the root level on a JSON Schema validation (#133)

## v1.8.0 - (2021-08-26)

- Added support for Postman Workspace when uploading collections (#118)
- Bug fix where portmanReplacements & upload to Postman had different results (#130)
- Improve output for CI and smaller terminals (#126)
- Updated example

## v1.7.0 - (2021-08-02)

### Enhancement

- Added overwrite `overwriteRequestSecurity` to be able to fine tune auth on a request level. This allows you to (for example) ensure all operations are authenticated via variation tests.

## v1.6.2 - (2021-08-02)

### Housekeeping

- remove console.log from variable injection

## v1.6.1 - (2021-07-30)

- Environment variables prefixed with `PORTMAN_` will be added to the Collection variables. This allows CI/CD to handle dynamic injection of values that should not be commited to repo.

### Enhancement

## v1.6.0 - (2021-07-28)

### Enhancement

- Added optional `bundleContractTests` to PortmanOptions that will take all operations that have contract tests applied, and move them to a 'Contract Test' folder on the root of the generated Collection
- Any operations that _do not_ have any contract tests will remain in their original place on the Collection

## v1.5.2 - (2021-07-27)

### Bugfix

- Fix for proper handling of contract tests with "enabled:false" during tests generation (#115).

## v1.5.1 - (2021-07-26)

### Bugfix

- Replaced instances where we were spreading arrays until we can safely upgrade packages that rely on outdated tslib

## v1.5.0 - (2021-07-23)

### Enhancement

- Added SecurityOverwrite options for methods: apiKey, Bearer Token & basic auth (#106)

### Bugfix

- Fix for the issue "spreadArray is not a function" since the \_\_spreadArrays function for TypeScript has been deprecated (#99)

## v1.4.4 - (2021-07-22)

### Enhancement

- Updated docs with an example for filtering
- Bumped openapi-format to 1.2.5
- Fix to prevent the unwanted addition 'Variation Tests'

## v1.4.3 - (2021-07-22)

### Bugfix

- Fix conflicting prompt alias that would not allow `--local` to be passed in as cli argument

## v1.4.2 - (2021-07-20)

### Enhancement

- Optimised the upload to postman process (#41)

### Bugfix

- Fix to handle invalid postmanUid impacting the upload to Postman (#88)

## v1.4.1 - (2021-07-19)

### Enhancement

- Portman exit codes have been changed to `exit(1)` to make it easier for external processes running Portman to distinguish fail vs. done.

## v1.4.0 - (2021-07-16)

### Enhancement

- Phased out "node-fetch" in favour of "Axios" + improved error handling for remote OAS files
- `newmanRunOptions` can now be passed as an object via cli argument `--newmanRunOptions`, or cliOptionsFile. This will be used to extend/overwrite Portmans default Newman options. 🎉

## v1.3.3 - (2021-07-14)

### Temporary fix

- Temporary fix for handling multiple content-types, where the contract will be based on the 1st content-type that is defined in the OpenAPI response.

## v1.3.2 - (2021-07-09)

### Globals

- Added option to define `portmanReplacements` for handling search & replace values after the Portman injection.

### Bug Fix

- Fix to handle remote sources ending with a trailing /

## v1.3.1 - (2021-07-09)

### Config Validation

- use draft06 for schema validation

## v1.3.0 - (2021-07-09)

### Portman Config

- Use AJV and [@apideck-libraries/better-ajv-errors](https://github.com/apideck-libraries/better-ajv-errors) to validate your Portman Config file on run

## v1.2.2 - (2021-07-09)

### Bug Fix

- Typo correction in readme
- Remove empty orderOfOperations from default config

## v1.2.1 - (2021-06-30)

### Housekeeping

- remove console log that snuck in where it shouldn't be

## v1.2.0 - (2021-06-30)

### Feature Release

#### Integration Tests

- Added ability to create Integration Tests within postman collection by ordering operations and tests specific to api implementation

#### PreRequest Scripts

- Added ability to configure PreRequest Scripts on an operation level

## v1.1.3 - (2021-07-02)

### Bug Fix

- global overrides now happen as soon as spec is converted to Postman collection to avoid infighting amount overwrites and injections

## v1.1.2 - (2021-07-01)

### Variation Tests

- Optimize overwrites for variations

## v1.1.1 - (2021-06-30)

### Variation Tests

- Fix to ensure overwrites for variations are not overwritten when running globals

### CLI

- Fix incomplete Postman collection when using --localPostman CLI options

## v1.1.0 - (2021-06-30)

### Operation Selectors

- new `openApiOperationsIds` setting can be passed as an array to selector operations for Portman to act on.

### CLI

- Added the option to upload a generated local postman collection and skip the Portman conversion

## v1.0.6 - (2021-06-30)

### CLI

- Added the option to load an existing postman collection and skip the openAPI to postman conversion

## v1.0.5 - (2021-06-29)

### Dependencies

- Added prompts package

## v1.0.4 - (2021-06-29)

### Dependencies

- move dev dependencies in package.json

## v1.0.3 - (2021-06-29)

### Dependencies

- updated postman-collection and others

## v1.0.2 - (2021-06-21)

### Bug Fixes

- contentTests that check against variables should use collectionVariables instead of environment variables

### Variation Tests

- nested folders (including variation tests) will be ignored when performing orderOfOperations
- Added statusCode tests for variations based on the openApiResponse property

## v1.0.1 - (2021-06-18)

### Overwrites

- extend overwrites to allow injection of objects and not just primitive values

## v1.0.0 - (2021-06-18)

## First Release

- Major overhaul from base release
- All features listed below

Added:

- [x] Convert an OpenAPI document to a Postman collection
  - [x] Support for OpenAPI 3.0
- Extend the Postman collection with capabilities
  - [x] Assign collection variables
    - [x] from ENV file
    - [x] from response body properties
    - [x] from response header properties
    - [x] from request body properties
  - [x] Inject Postman contract tests with
    - [x] HTTP response code validation
    - [x] Response time validation
    - [x] Response content-type validation
    - [x] Response JSON body validation
    - [x] Response JSON schema validation
    - [x] Response content validation
    - [x] Custom Postman tests
  - [x] Inject Postman variation tests for
    - [x] HTTP response code validation
    - [x] Response time validation
    - [x] Response content-type validation
    - [x] Response JSON body validation
    - [x] Response JSON schema validation
    - [x] Response content validation
    - [x] Custom Postman tests
  - [x] Inject Postman with
    - [x] Pre-request scripts on a collection level
  - [x] Modify Postman requests by
    - [x] Overwriting request path variables
    - [x] Overwriting request query params
    - [x] Overwriting request headers
    - [x] Overwriting request body
    - [x] Replace keywords with custom defined keys
    - [x] Replace values with custom defined values
    - [x] Search & replace any key/value with a specific value
    - [x] Order the collections requests
- [x] Upload the Postman collection to your Postman app
- [x] Test the Postman collection through Newman
- [x] Manage everything in config file for easy local or CI/CD usage

## v0.1.0 - (2021-05-31)

### OpenApi-Format / CLI options

- Added CLI Option filterFile to pass path to filter options for ignoring requests in spec before passing to Postman conversion

## v0.0.9 - (2021-05-28)

### CLI options

- Added CLI Option `envFile` to pass a path to `.env` that Portman should use for variable injection

## v0.0.8 - (2021-05-28)

### Newman

- Set Newman option to ignore redirects

## v0.0.7 - (2021-05-25)

### OpenApi-to-postman

- Corrected the incorrect "checkRequestBody" variable definition to "checkResponseBody"
- Let testsuite overwriteRequests handle the disabling of params

## v0.0.6 - (2021-05-25)

### CLI options

- Resolve issue with overriding paths to defaults when not provided
- Extended hardcoded list of params to disable until they are passed in as config

## v0.0.5 - (2021-05-25)

### OpenApi-to-postman

- Bumped openapi-to-postman to the latest version, which includes extended assignPmVariables test capabilities
- Added examples for the test suite assignPmVariables function
- Added examples for the test suite overwriteRequests function

## v0.0.4 - (2021-05-18)

### OpenApi-to-postman

- Bumped openapi-to-postman to version 2.7.0, which includes ContentCheck test capabilities
- Added examples for the test suite generation
- Added examples for the test suite contentChecks function
- Made the "orderOfOperations" property optional

### CLI options

- Adds the CLI option to configure the Portman CLI in a JSON file
- Adds the CLI option to configure output location of the Postman file
- Adds the CLI option to toggle upload to Postman

### Portman enhancements

- Adds the Portman option to sort Postman requests based on the "orderOfOperations" configuration
- Extends the Postman integration to upsert a collection based on the collection name

## v0.0.3 - (2021-05-06)

- Adds CLI options to pass in path to config files allowing multiple CIs to live in the same repo.

## v0.0.2 - (2021-05-06)

- Updates repo url to public repo

## v0.0.1 - (2021-05-06)

- Base release
