# General e-Commerce Guide

**Table of Contents**

- [Structure](#structure)
- [Blocks](#blocks)
- [Simple Pages](#simple-pages)
- [Commerce Pages (Customer)](#commerce-pages-customer)
- [Commerce Pages (Admin)](#commerce-pages-admin)
- [Emails](#emails)
- [Search](#search)
- [Other](#other)
- [Drupal Modules](#drupal-modules)
- [Resources](#resources)

---

## Structure

- **Product Display** (entity or node for 7.x)
  - Text Fields
  - Taxonomies (brand, category, display taxonomy, season etc)
  - Translations
  - Images
  - Share on social networks buttons
  - Metatag (schema.org)
  - Product reviews
  - Add to favorites

- **Product Variation** (entity)
  - Price
  - List price
  - Shippable/Non-shippable
  - Name pattern
  - Stock (inventory)
  - Attributes (size, color, etc)
  - Weight
  - Ask for this Product link
  - Out of Stock message
  - See also list (related Products)
  - Product bundles (packages of Products sold as a single item)
  - Product gifts (free Products when you buy other Products)

- **Payment types**
  - Cash on delivery
  - Cash on store
  - Bank transfer (deposit)
  - Paypal
  - Credit/debit card payment (bank APIs, Stripe etc)

- **Shipping methods**
  - Store pickup
  - Courier (get rates API or set flat rates)
  - Free shipping
  - Custom (by arrangement)

- **Order**
  - Notes/Comments
  - Shipping tracking key/ID
  - PDF attachment (order or invoice attachment)
  - Guest checkout
  - Taxes setup
  - Allowed Countries for shipping

- **Customer Profile**
  - Shipping
  - Billing

---

## Blocks

- Breadcrumbs
- System messages
- Search form (text input)
- Search facets
- Cart
- Login/Register
- Checkout step indicator
- Free shipping banner
- Info about Shipping costs and time
- Info about Payment methods
- Info about Discounts
- Info about Quarantee
- Info about Secure transactions
- Info about Store physical address
- Contact info
- Newsletter subscribe form
- Social profiles info and links (follow us)
- Instant messaging and support widget (real user or chatbot)
- Dynamic: Latest Products
- Dynamic: Popular Products
- Dynamic: Editor picks Products
- Dynamic: Promoted Products
- Dynamic: Related Products (by reference or search query)
- Dynamic: Recently viewed Products (Last seen)

---

## Simple Pages

- Shipping
- Payments
- Returns
- Our Store/Company
- FAQs
- Terms of use and legal contents
- Measuring, sizes etc
- Contact form and info

---

## Commerce Pages (Customer)

- Checkout pages (with steps)
- My Order(s)
- My favorite Products
- My Account
- My Addresses (Billing, Shipping)
- Return a Product form (or pdf application)
- Create Account
- Complete Order Thank-you landing page

---

## Commerce Pages (Admin)

- Shop overview/dashboard
- Orders
- Products
- Product Varations
- Customer profiles
- Discounts/Promotions
- Coupons, Gift cards, Loyality points etc

---

## Emails

Emails as also as SMS and Mobile App messages (eg WhatsApp)

- New Order created (Customer)
- New Order created (Admin)
- Order sent with courier with tracking info (Customer)
- Order canceled (Customer)
- Order abandoned (Customer)
- Product Variation is out of stock (Admin)

---

## Search

- External service (SOLR, Elastic, Algolia, Sajari) vs core Views
- Autocomplete (ajax)
- Suggestions for keywords
- Suggestions for wrong (eg misspelling) input
- No results message
- Search API: stemmer
- Search API: stopwords
- Search API: ignore case/characters
- Search API: partial search (tokenizer)
- Search API: greeklish
- Search API: smallcase
- Search API: Boost by tag (HTML filter)
- Facets: Taxonomy
- Facets: Price
- Facets: Attributes
- Disallow empty results (consequence filtering)
- Voice search input

[Article 1](https://www.easternstandard.com/node/1049), [Article 2](https://www.axelerant.com/resources/team-blog/test-scenarios-search-functionality-drupal)

---

## Other

- Product
  - path aliases
  - metatags
  - tell a friend
  - Customer reviews or comments
  
- Customer
  - Favorite Products
  - Login with social profile (Google, FB, Apple etc)
  - Wholesame customers

- Order
  - (google) analytics for commerce orders
  - SMS on complete payment transaction (for e-payments)
  - Abandoned Cart Reminder
  - Repeat an Order
  - Create Order through url arguments
  - Online Invoices

- Store
  - Currencies
  - Customer reviews
  - Skroutz API status and xml
  - Export data (orders, customers, income etc)
  - CRM, Logistics external integration (2 way sync)
  - Integration with 3rd party services (marketing, newsletters, user tracking, analytics, payments, shipping etc)

- Website
  - Translations
  - SSL
  - sitemap.xml
  - gdpr cookies banner
  - cron setup for search index and sitemap
  - CDN and fast hosting

---

## Drupal Modules

Interesting Drupal modules for e-commerce websites:

 - https://www.drupal.org/project/commerce, https://docs.drupalcommerce.org
 - https://www.drupal.org/project/digital_marketing_checklist

---

## Resources

- [Book: Digital Marketing with Drupal, 03/2022](https://www.packtpub.com/product/digital-marketing-with-drupal/9781801071895)
- [How to Build a B2B eCommerce Marketplace with Drupal Commerce (2023)](https://lembergsolutions.com/blog/how-build-b2b-ecommerce-marketplace-drupal-commerce)
- [astrotars/awesome-ecommerce-stack](https://github.com/astrotars/awesome-ecommerce-stack)
