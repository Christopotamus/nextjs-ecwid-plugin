# Ecwid Ecommerce Shopping Cart
Powerful, easy to use ecommerce shopping cart plugin for Next.js sites. Over 1 million sellers in 175 countries, 45 languages supported. PayPal, Stripe and 40 more payment options. Real-time shipping integrations. Selling on Instagram and Facebook.

## Installation

    npm install @ecwid/nextjs-ecwid-plugin

### Usage 

Create a wrapper for the EcwidProvider and give it your storeId as a key in the value object.

```javascript
"use client"
import {EcwidProvider} from '@ecwid/nextjs-ecwid-plugin';

export const EcwidProviderWrapper = ({ value, children }) => {
  return (
    <EcwidProvider value={{ storeId: process.env.NEXT_PUBLIC_ECWID_STORE_ID }}>
      {children}
    </EcwidProvider>
  );
}

export default EcwidProviderWrapper;
```

If the provider wraps your whole app (e.g. in the root layout) and the store lives on its own page, pass that page's path as `baseUrl`. Ecwid otherwise builds product URLs from whichever page its script first loaded on, so a visitor who starts on `/` and navigates to `/store` would get product links under `/`.

```javascript
<EcwidProvider value={{ storeId: process.env.NEXT_PUBLIC_ECWID_STORE_ID, baseUrl: '/store' }}>
```

Add this to your component or layout:

```javascript
<html lang="en">
    <body>
        <EcwidProviderWrapper>
            {children}
        </EcwidProviderWrapper>
    </body>
</html>

```

In your app, use the ProductBrowser or BuyNowButton components.

ProductBrowser usage example:
```javascript
import {ProductBrowser} from '@ecwid/nextjs-ecwid-plugin'

export default function Store() {
  return (
    <>
      <ProductBrowser />
    </>
  )
}
``` 

Buy Now Button usage example:
```javascript
import {BuyNowButton} from '@ecwid/nextjs-ecwid-plugin'

export default function Store() {
  return (
    <>
      <BuyNowButton
        productId="102852327"
        isShowPrice={false}
      />
    </>
  )
}
``` 

## License

This project is [Apache2.0](LICENSE) licensed.
