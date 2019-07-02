---
title: Context Configuration (DRAFT)
---

The `context` parameter allows for the configuration of the application by appending attribute values to the Storefront URL.
In addition to this, it provides the flexibility of being able to change these values dynamically.

**Ex**: Assume a `language` attribute is used and its value is set to English.
When the application is loaded, the Storefront URL will contain this property and the translations provided will be in English.

`context` can be found in the `app.module.ts` and looks as such:

```typescript
  context: {
      parameters: {
        baseSite: {
          values: [
            'electronics-spa',
            'electronics',
            'apparel-de',
            'apparel-uk',
          ],
          persistence: 'route',
        },
      },
    urlEncodingParameters: ['baseSite', 'language', 'currency'],
  },
 ...
```

For a better understanding of how these properties work, each one will be explained.

### Parameters

The `parameters` property will take a list of attributes and their defined values.

The definition for `language` is provided below:

```typescript
 parameters: {
        [language]: {
          values: ['en', 'de', 'ja', 'zh'],
          default: 'en',
          persistence: 'route',
        },
        ...
```

#### Values

`values` will take a list of potential values that can be used by the application.
This property provides the capability of switching between values when required.

In the case above, the languages available are `en (English), de (German), ja (Japanese), and zh (Chinese)`.

**Note**: If there is no `default` value provided, the default value will be the first argument in the list which is `en (English)` in this case.

#### Default

`default` selects the specific option for the application when it is first loaded.

In the case above, the default language is `en (English)`.

**Note**: The `default` must be in the list of `values` provided.

#### Persistence

`persistence` determines when the context attributes are applied.
When `route` is used, these arguments will appear throughout the entire application.

In the case above, the value is set to `route` and therefore it is applied site-wide.

#### urlEncodingParameters

`urlEncodingParameters` will take a list of arguments that will be used to produce the context. The context is then appended to the Storefront
URL.

Assume that the Storefront URL is `https://localhost:4200`.

Assume the configuration is as follows:

```typescript
  context: {
      parameters: {
        baseSite: {
          values: [
            'electronics-spa', //Selected by default as it is the first argument in the list
            'electronics',
          ],
          persistence: 'route',
        },
        language: {
          values: [
            'en'
          ],
          persistence: 'route',
        },
        currency: {
          values: [
            'USD'
          ],
          persistence: 'route',
        },
      },
    urlEncodingParameters: ['baseSite', 'language', 'currency'],
  },
 ...
```

The result of this will be `https://localhost:4200/electronics-spa/en/USD`.