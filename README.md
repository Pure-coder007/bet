# ATA lead routing

This landing page now supports lead-specific affiliate routing from one shared `index.html`.

## How it works

- A visitor can arrive on `/lead1`, `/lead2`, `/lead2u`, or `/?lead=lead1`.
- The page reads the lead slug from the path or query string.
- Every CTA uses that lead's assigned 1xBet affiliate link.
- A basic `dataLayer`/`gtag` event is pushed for page views, video opens, and affiliate redirects.

## Where to update links

Edit the `leadAffiliateLinks` object in [index.html](./index.html).

```js
const leadAffiliateLinks = {
  default: "https://1xbet.com/?ref=ATA_TRACKING_ID",
  lead1: "https://reffpa.com/L?tag=d_5551353m_97c_lead1",
  lead2: "https://reffpa.com/L?tag=d_5551353m_97c_lead2",
  lead2u: "https://reffpa.com/L?tag=d_5551353m_97c_lead2U",
  lead3g: "https://reffpa.com/L?tag=d_5551353m_97c_lead3G",
  lead4i: "https://reffpa.com/L?tag=d_5551353m_97c_lead4I",
  lead5p: "https://reffpa.com/L?tag=d_5551353m_97c_lead5P",
  lead6m: "https://reffpa.com/L?tag=d_5551353m_97c_lead6M",
  lead7z: "https://reffpa.com/L?tag=d_5551353m_97c_lead7z",
  lead8c: "https://reffpa.com/L?tag=d_5551353m_97c_lead8c"
};
```

Lead slugs are normalized to lowercase, so use URLs such as `/lead2u`, `/lead3g`, and `/lead6m`.

## Routing note

Pretty URLs like `/lead1` or `/lead2u` still need host-level rewrites to `index.html` for the cleanest setup.

`404.html` was added as a static-host fallback so some platforms can recover `/slug` requests by redirecting them to `/?lead=slug`.
