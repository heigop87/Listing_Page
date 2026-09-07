*Last update: 7 September 2026*
*Business Analysts: per the row's BA Owner*
*Design: [heigop87.github.io/Listing_Page](https://heigop87.github.io/Listing_Page/), annotated prototype · numbered positions at [/notes/](https://heigop87.github.io/Listing_Page/notes/) · styled on @yachtway/ui*
*Platform: Web and mobile web*

<callout icon="⛵">
	**Build spec for the active vessel page at `/brands/[brand]-yachts-for-sale/[model]/[year]-[model]-[id]/`. The page layout lives here: [heigop87.github.io/Listing_Page](https://heigop87.github.io/Listing_Page/), every module, CTA and rule annotated in place at [/notes/](https://heigop87.github.io/Listing_Page/notes/). Read it before this document.** Status, the internal ID specification, the sold state and the lane to do lists live on the Listing pages row. Evidence and benchmark history live on [Listing Page · Information Hierarchy](https://app.notion.com/p/3d46d212272c81eba767d58be755ac4c). URL rules, breadcrumb, robots and query keys follow the [Site link tree](https://app.notion.com/p/3ca6d212272c8108a447cef78322c677), which wins on any disagreement. Field lists inside the specification tabs, the gallery popup, the tour modal, Save, Share and Ask Waylo behave as written in Listing Page Guest.
</callout>

## Page order and text

**The page as it renders, with every rule annotated in place:** [heigop87.github.io/Listing_Page](https://heigop87.github.io/Listing_Page/), repo `heigop87/Listing_Page`. Toggle **Notes** for the numbered positions. Same visual language as the Home, Catalog and Brand prototypes, on @yachtway/ui tokens. Prototype data. On order the prototype wins; on wording the sections below win.

```javascript
Header · nav 4 · EN · Sell · Log in or sign up · Home Page PRD
BC   Home › Brands › [Brand] › [Brand Model] › [Year Brand Model]
H1   [Year] [Brand Model] For Sale
     Meta line · status · condition · length · hours · location · badge · views
     Gallery hero, full width · cover · video · 3D tour · photos · deck layout
     Sticky section nav, full width · 9 anchors · Save · Share · Price alert
     ── two columns from here · content left · contact block sticky right ──
     Price card · Condition card
     Four-stat strip · Length · Top speed · Range · Hours
H2   About this [Brand Model] · highlight · description · ownership strip · activities
H2   What This Boat Comes With · 6 shown · Show all
H2   [Year Brand Model] Specifications · US | Metric · 6 tabs
H2   Deck Layout · conditional
EYE  NautiX · H2 How Far Can This Boat Actually Go? · map · chips · speed slider
H2   Ask Waylo About This Boat
EYE  Is the price fair · H2 [Year Brand Model] Price and Value · 6 cards
EYE  Can I afford it · H2 Finance and Insure This Boat · calculator · pre-qualify · insurance
EYE  YachtWay Spotlight · H2 [Brand Model] Video Review · conditional
H2   Seller · facts · Visit seller profile · Contact seller
H2   Events for This Boat · conditional
H2   Other [Seller] Listings · 6 cards · All [n] [Seller] listings
H3   Download the PDF for this [Year Brand Model]
H2   Frequently Asked Questions · optional
     All [noun] for sale · pillar anchor
H3   Popular Searches · footer · Home Page PRD
```

**Mobile, under 900 px:** one column in the same order, contact card under the four-stat strip. Bottom bar with price, **Call**, **Request info** from the first viewport. **Ask Waylo** pill fixed lower left. Nav wraps to two rows, never scrolls sideways.

**Nothing else renders text.** No similar vessels from another seller, no model page banner, no response rate or response time, no dealer label on the contact card, no media count chips under the gallery, no trip counts, no YouTube rail.

### Every string, with its destination and render

Header, pre-footer and footer are sitewide: Home Page PRD rows 1 to 9 and 48 to 53. Not restated.

<table fit-page-width="true" header-row="true">
<tr><td>#</td><td>Text</td><td>Element</td><td>Goes to</td><td>Render</td></tr>
<tr><td>1</td><td>Home › Brands › [Brand] › [Brand Model]</td><td>Breadcrumb anchors, four</td><td>`/` · `/brands/` · `/brands/[brand]-yachts-for-sale/` · `/brands/[brand]-yachts-for-sale/[model]/`</td><td>Server. Identical for every entry path</td></tr>
<tr><td>2</td><td>[Year Brand Model]</td><td>Breadcrumb current, plain text</td><td></td><td>Server</td></tr>
<tr><td>3</td><td>**[Year] [Brand Model] For Sale**</td><td>**H1, the only one**</td><td></td><td>Server, from the record, never from click path</td></tr>
<tr><td>4</td><td>For sale · Pre-owned · 72 ft · 410 h · **Miami, FL** · Authorized Dealer · 1,240 views</td><td>Meta line. Location is the one anchor</td><td>`/miami-fl-yachts-for-sale/`</td><td>Server. Hours absent on New. Badge absent for Brokerage Firms</td></tr>
<tr><td>5</td><td>[n] photos · Video · 3D tour · Deck layout</td><td>Gallery tiles, buttons, one label each</td><td>Gallery popup on that tab</td><td>Server tiles. Tiles with no content absent</td></tr>
<tr><td>6</td><td>This listing has a 3D tour · Start 3D tour</td><td>3D tile label and button</td><td>3D tour viewer</td><td>Server. Under 900 px the label reads 3D tour, no button</td></tr>
<tr><td>7</td><td>See all media</td><td>Button on the cover</td><td>Gallery popup, Photos tab</td><td>Server</td></tr>
<tr><td>8</td><td>Gallery · Overview · Features · Specs · NautiX · Value · Financing · Seller · More from seller</td><td>Sticky nav anchors, left</td><td>Same page anchors</td><td>Server. Active anchor underlined on scroll</td></tr>
<tr><td>9</td><td>Save · Share · Price alert</td><td>Icon buttons with tooltips, right of the nav</td><td>Save, Share, Get Price Alert modal</td><td>Server. Price alert absent on hidden price</td></tr>
<tr><td>10</td><td>Price reduced</td><td>Pill, price card</td><td></td><td>Server, only with a recorded drop inside the 48 hour and hidden price rules</td></tr>
<tr><td>11</td><td>$1,650,000 · ~~$1,745,000~~ · Down $95,000 on 14 Aug</td><td>Price card figures</td><td></td><td>Server. *Price on application* replaces all three when hidden</td></tr>
<tr><td>12</td><td>Est. $14,900 / mo · Get your rate · no credit impact</td><td>Price card anchor</td><td>Financing module</td><td>Server. Absent where the calculator is hidden</td></tr>
<tr><td>13</td><td>Pre-owned, 1 owner · 410 engine hours · Captain maintained · Never chartered</td><td>Condition card, two lines</td><td></td><td>Server. Only set flags</td></tr>
<tr><td>14</td><td>72 ft Length · 32 kn Top speed · 320 nm Range, plan a trip · 410 h Hours</td><td>Four-stat strip. Range is the one anchor</td><td>NautiX module</td><td>Server. A stat with no value is omitted</td></tr>
<tr><td>15</td><td>[Seller name] · [City, jurisdiction]</td><td>Contact card head, verified icon where Authorized Dealer or Factory Direct</td><td></td><td>Server. Seller name plain text here</td></tr>
<tr><td>16</td><td>Show phone number</td><td>Button</td><td>Reveals the number, second click `tel:`</td><td>Server</td></tr>
<tr><td>17</td><td>WhatsApp</td><td>Anchor</td><td>WhatsApp with the availability message</td><td>Server, only where the seller has a WhatsApp number</td></tr>
<tr><td>18</td><td>Full name · Email · Phone · Message · Request info</td><td>Form, four fields and submit</td><td>Inquiry to the seller</td><td>Server</td></tr>
<tr><td>19</td><td>Earliest viewing [day time], vessel local time · Schedule a tour</td><td>Line and button</td><td>Tour modal</td><td>Server</td></tr>
<tr><td>20</td><td>Est. $14,900 / mo, 20% down, 20 years, 7.5% · Get your rate</td><td>Contact card line and button</td><td>Financing module</td><td>Server. Absent where the calculator is hidden</td></tr>
<tr><td>21</td><td>**About this [Brand Model]**</td><td>H2</td><td></td><td>Server</td></tr>
<tr><td>22</td><td>Seller highlight · description · Read more</td><td>Callout, body, button</td><td>Expands in place</td><td>Server, full text in the HTML. Brand name is the one inline anchor</td></tr>
<tr><td>23</td><td>US duty paid · Tax not paid · Engine warranty to Mar 2027 · Available now</td><td>Ownership chips, plain text</td><td></td><td>Server. Unknown values omitted</td></tr>
<tr><td>24</td><td>**What This Boat Comes With** · Show all [n] features</td><td>H2, button</td><td>Expands in place</td><td>Server, every feature in the HTML</td></tr>
<tr><td>25</td><td>**[Year Brand Model] Specifications** · US | Metric</td><td>H2, toggle</td><td>Client state, remembered per visitor</td><td>Server H2. Toggle visible on Measurements and Tanks only</td></tr>
<tr><td>26</td><td>General · Measurements · Engines · Accommodation · Tanks · Extra details · Rigging</td><td>Tabs. Rigging for sail only</td><td></td><td>Server, every panel in the HTML</td></tr>
<tr><td>27</td><td>**Deck Layout**</td><td>H2, conditional</td><td>Gallery popup, Deck Layout tab</td><td>Server, absent with no deck image</td></tr>
<tr><td>28</td><td>NautiX · YachtWay's range planner · **How Far Can This Boat Actually Go?**</td><td>Eyebrow, H2</td><td></td><td>Server</td></tr>
<tr><td>29</td><td>Popular trips from [Port] · four place chips · Cruising speed [n] kn</td><td>Chips, slider</td><td>Sets A and B on the map</td><td>Server chips, client map. No counts</td></tr>
<tr><td>30</td><td>Route · Distance · Trip time · Fuel burned · Tank on arrival · Fits in range · basis line</td><td>Outputs</td><td></td><td>Client from record data. Basis line server</td></tr>
<tr><td>31</td><td>**Ask Waylo About This Boat** · Ask · four suggested questions</td><td>H2, button, chips</td><td>Waylo</td><td>Server</td></tr>
<tr><td>32</td><td>Is the price fair · **[Year Brand Model] Price and Value** · Age · Engine · Options and features · Warranty · Price history · Other market factors</td><td>Eyebrow, H2, six cards</td><td></td><td>Server. No price figure when hidden</td></tr>
<tr><td>33</td><td>Can I afford it · **Finance and Insure This Boat**</td><td>Eyebrow, H2</td><td></td><td>Server. Whole section absent per section 15</td></tr>
<tr><td>34</td><td>Price · Down payment % · Term · Rate % · Est. monthly payment · Down payment · Credit range</td><td>Calculator fields and result</td><td></td><td>Server fields, client result</td></tr>
<tr><td>35</td><td>Get pre-qualified for this boat</td><td>CTA</td><td>`/easy-fund/get-prequalified-internal-vessel/[listingId]/`</td><td>Server</td></tr>
<tr><td>36</td><td>**Insure this [Brand Model]** · Get an insurance estimate</td><td>H3, CTA</td><td>MasterCover with the hull prefilled</td><td>Server</td></tr>
<tr><td>37</td><td>YachtWay Spotlight · **[Brand Model] Video Review** · Watch the [Brand Model] video review</td><td>Eyebrow, H2, one card anchor</td><td>`/brands/[brand]-yachts-for-sale/[model]/video-review/`</td><td>Server, only where a Spotlight exists</td></tr>
<tr><td>38</td><td>**Seller** · Listings · Authorized dealer of · Member since · Offices · Visit seller profile · Contact seller</td><td>H2, four facts, two CTAs</td><td>`/dealers/[seller]/` · contact block</td><td>Server</td></tr>
<tr><td>39</td><td>**Events for This Boat** · Set a reminder · Request RSVP</td><td>H2, cards, CTAs</td><td>Event modals</td><td>Server, absent with no current or future event</td></tr>
<tr><td>40</td><td>**Other [Seller] Listings** · Year Make Model, six · All [n] [Seller] listings</td><td>H2, card anchors, anchor</td><td>The listings · `/dealers/[seller]/`</td><td>Server. Price, city, badge outside the anchor</td></tr>
<tr><td>41</td><td>Download the PDF for this [Year Brand Model] · Download PDF</td><td>H3, button</td><td>PDF</td><td>Server</td></tr>
<tr><td>42</td><td>**Frequently Asked Questions** · one H3 per question</td><td>H2, details</td><td></td><td>Server, answers in the HTML while collapsed</td></tr>
<tr><td>43</td><td>All [noun] for sale</td><td>Pillar anchor, footer edge</td><td>`/yachts-for-sale/` or `/boats-for-sale/` by length</td><td>Server</td></tr>
<tr><td>44</td><td>Price · Year Brand Model · Call · Request info</td><td>Mobile bottom bar</td><td>`tel:` · Request info modal</td><td>Server, under 900 px</td></tr>
<tr><td>45</td><td>Ask Waylo</td><td>Mobile sticky pill, lower left</td><td>Ask Waylo module</td><td>Server, under 900 px</td></tr>
</table>

---

**Acceptance Criteria**

GIVEN I am a **Customer** or an **Unlogged User** who opened a vessel listing from a catalog card, a brand, model, type, location or dealer page, a video, a shared link or a search result
WHEN the page loads
THEN I see the canonical breadcrumb, one H1, the gallery, the price and the seller's phone, Request info and Schedule a tour controls without scrolling, on desktop and on mobile, every module below in the order above, and nothing from any other seller.

## Launch gates

<table fit-page-width="true" header-row="true">
<tr><td>Gate</td><td>Closed when</td></tr>
<tr><td>**G1. Contact reach**</td><td>Phone, Request info and Schedule a tour sit in the first viewport at 402 px and stay on screen at every scroll position at 1440 px</td></tr>
<tr><td>**G2. Identity**</td><td>One H1. The visible breadcrumb string equals `BreadcrumbList` and is identical from every entry path. The final URL segment matches the internal ID pattern; no HIN in any URL</td></tr>
<tr><td>**G3. Rendering**</td><td>View source with JavaScript off contains every heading, spec panel, feature, FAQ answer and anchor. Zero content injected on click</td></tr>
<tr><td>**G4. Seller exclusivity**</td><td>Zero listings from another seller, zero model page banner, zero response metrics, zero trip counts</td></tr>
<tr><td>**G5. Pre-qualification**</td><td>One click from the listing reaches the EasyFund first step with the hull prefilled, and EF Prequal Submitted carries `listing_id`</td></tr>
<tr><td>**G6. Hidden price**</td><td>A hidden price listing shows Price on application everywhere, no drop, no estimate, no price in the message, no Price alert, no price in the Offer</td></tr>
</table>

### 1. Identity and head {color="blue_bg"}

<table fit-page-width="true" header-row="true">
<tr><td>Field</td><td>Value</td></tr>
<tr><td>URL</td><td>`/brands/[brand]-yachts-for-sale/[model]/[year]-[model]-[id]/`. Internal ID per the row, eight Crockford Base32 characters, never the HIN. Every live `/vessels/` URL 301s here in one hop</td></tr>
<tr><td>Title</td><td>**[Year] [Brand Model] For Sale \| YachtWay**</td></tr>
<tr><td>Meta description</td><td>*[Year] [Brand Model] for sale in [City, jurisdiction]. [Price or Price on application], [LOA], [n] engine hours. Listed by [Seller] on YachtWay.* Hours clause absent on New</td></tr>
<tr><td>H1</td><td>**[Year] [Brand Model] For Sale**. Exactly one. From the record, never from click path or filter state</td></tr>
<tr><td>Breadcrumb</td><td>Home › Brands › [Brand] › [Brand Model] › [Year Brand Model]. Same string in `BreadcrumbList`. The only structural link up</td></tr>
<tr><td>Robots</td><td>index, follow. Self canonical. hreflang six locales plus x-default. Hidden price listings may sit lower in the sitemap or out of it</td></tr>
<tr><td>Schema</td><td>`Product` with `Offer` (price, currency, availability InStock), `BreadcrumbList`. `FAQPage` only where the FAQ renders. `vehicleIdentificationNumber` only when the HIN is real, `sku` off the internal ID. Geo omitted when coordinates are absent or 0,0. No `VideoObject` for the Spotlight review; the review page holds it. Hidden price: `Offer` without `price`</td></tr>
<tr><td>Never in title, H1 or canonical</td><td>HIN, dealer, condition, generation, location, boat or yacht as a word</td></tr>
</table>

**Done when** the canonical, breadcrumb and H1 are generated from the record alone, and *undefined* appears in no head tag or JSON-LD field.

### 2. Rendering {color="blue_bg"}

1. Every module, anchor, spec panel, feature, FAQ answer and the contact form are server rendered. Collapsed content sits in the HTML, never injected on click.
2. Client state only for: gallery popup, unit toggle, spec tab selection, NautiX map and outputs, loan result, Read more, Show all features, Save, Share, modals.
3. Conditional modules are absent from the HTML when their condition fails. No empty heading, placeholder or container.
4. Every card is an `a` with an `href`. Icon only controls carry an accessible name.

**Done when** view source with JavaScript off shows every heading and anchor in the page order, and every conditional module is either complete or absent.

### 3. Meta line {color="purple"}

One line under the H1, wrapping on mobile, items separated by a dot, in this order:

1. **Status** - pill: For sale, Sale pending. Sold per the row
2. **Condition** - New or Pre-owned
3. **Length** - LOA, follows the unit toggle
4. **Engine hours** - average across engines. **NOT shown** for New
5. **Location** - City, jurisdiction per Site link tree rule 9, the one anchor, to the location page
6. **Authorized Dealer** or **Factory Direct** badge. **NOT shown** for Brokerage Firms
7. **Views** - [n] views

**NOT on the meta line:** year, vessel name, cabins, type, fuel, speed.

### 4. Gallery hero {color="purple"}

1. Full page width. Cover tile plus four tiles: video, 3D tour, photos, deck layout. Each tile carries its own label; nothing renders beneath the gallery.
2. **3D tour tile** outlined and labelled **This listing has a 3D tour**, with **Start 3D tour** on the tile. Under 900 px the label reads **3D tour** and the button is dropped.
3. **See all media** opens the gallery popup per Listing Page Guest: Videos, 3D Tour, Photos, Deck Layout.
4. Tiles with no content are **NOT shown**; the grid collapses.

**Done when** the gallery is the only media entry above the fold and a listing with photos only renders a cover and a photo tile.

### 5. Sticky section nav {color="purple"}

1. Full page width directly under the gallery, above both columns. Sticks at the top on scroll. One row on desktop, no horizontal scrolling, wraps on narrow widths.
2. Anchors left, in page order: Gallery, Overview, Features, Specs, NautiX, Value, Financing, Seller, More from seller. Active anchor underlined as the reader passes each section.
3. Right side: **Save**, **Share**, **Price alert** as icon pills with tooltips. Save and Share per Listing Page Guest. **Price alert** opens the Get Price Alert modal, open price listings only.
4. **NOT in the nav:** Call, Request info, Back.

**Done when** the nav spans the page at 1440 px in one row and Save, Share and Price alert sit above the contact block.

### 6. Price card, condition card, four-stat strip {color="purple"}

**Price card**, dark surface:
1. **Price reduced** pill top right, only when a drop exists inside the 48 hour and hidden price rules.
2. Current price large, previous price struck through beside it, then **Down [amount] on [date]**.
3. **Est. [amount] / mo · Get your rate · no credit impact**, anchor to the Financing module. **NOT shown** where the calculator is hidden.
4. Price hidden: **Price on application** replaces the figure. No drop line, no estimate.

**Condition card:**
1. **[New or Pre-owned], [n] owner**
2. Engine hours · Captain maintained · Never chartered. Only the flags that are set

**Four-stat strip** under the two cards: **Length** (unit toggle) · **Top speed** kn · **Range** nm at cruise, manufacturer basis, anchor to NautiX · **Hours** average engine hours.

**Done when** a hidden price listing shows Price on application and no estimate, and every stat with no value is omitted rather than empty.

### 7. Contact block {color="blue_bg"}

Right column on desktop, sticky for the whole page, 64 px under the nav. On mobile a card under the four-stat strip plus the bottom bar.

1. **Seller name** with the verified icon where Authorized Dealer or Factory Direct applies, location beneath. Name is plain text here. **NOT shown:** dealer label text, response rate, response time.
2. **Show phone number** - first click reveals, second click calls.
3. **WhatsApp** - opens WhatsApp with the availability message. Shown only where the seller has a WhatsApp number.
4. Request info form:
   - **Full name** - text input, required, max 100 characters
   - **Email** - email input, required
   - **Phone** - tel input, optional
   - **Message** - textarea, pre-filled *"Hi, I'd like to know if the [Year Make Model] listed on YachtWay for [price] is still available."*, price clause omitted when hidden, max 1500 characters
   - **Request info** - submits, unlimited, toast *"The request has been sent to the Seller!"*
5. **Earliest viewing [day time], vessel local time** and **Schedule a tour**, tour modal per Listing Page Guest.
6. **Est. [amount] / mo, [down]% down, [years] years, [rate]%** and **Get your rate**, anchor to the Financing module. **NOT shown** where the calculator is hidden.

**Mobile bottom bar:** price and Year Brand Model left, **Call** and **Request info** right. **Ask Waylo** pill fixed lower left above the bar.

**Done when** G1 closes and the pre-filled message carries no price on a hidden price listing.

### 8. About this [Brand Model] {color="blue_bg"}

1. **Seller highlight** - callout, optional, from the record.
2. **Description** - about 400 words visible, **Read more** expands in place. Brand name is the one inline anchor, to the brand page.
3. **Ownership strip** - chips: **US duty paid** or **[Country] duty paid** · **Tax status** · **Engine warranty to [month year]** or the active warranty · **Available now** or **Available in [n] months**. Each chip **NOT shown** where the value is unknown.
4. **Activity chips** - from the record.

### 9. What This Boat Comes With {color="blue_bg"}

1. Features grid, six shown, three per row on desktop. **Show all [n] features** expands in place.
2. Section **NOT shown** when the listing has no features.

### 10. Specifications {color="blue_bg"}

1. H2 **[Year Brand Model] Specifications**.
2. **US | Metric** toggle, top right. Visible only while Measurements or Tanks is the active tab. Remembered per visitor. Applies to every length, weight and volume on the page, meta line and stat strip included. Default US.
3. Tabs in order: **General**, **Measurements**, **Engines**, **Accommodation**, **Tanks**, **Extra Details**, **Rigging** for sail. Every panel in the DOM at initial render. Field lists per Listing Page Guest, plus **Vessel name** in General. No Features tab.
4. Disclaimer beneath, persists across tabs, text per Listing Page Guest.

**Done when** switching to Metric changes the meta line length, the stat strip and every measurement in one action, and the toggle is absent on General.

### 11. Deck Layout {color="blue_bg"}

Conditional. One tile per deck image with a deck label, opens the gallery on the Deck Layout tab. The 3D tour is not here.

### 12. NautiX {color="blue_bg"}

Spec on the [NautiX row](https://app.notion.com/p/3d46d212272c815ea62fd5068986a00b). On the listing:

1. Eyebrow **NautiX · YachtWay's range planner**. H2 **How Far Can This Boat Actually Go?**
2. **Popular trips from [Port]** - four chips, the most planned routes from the vessel's port in internal NautiX usage. Counts **NOT shown**. Tap sets A and B.
3. Map: tap sets A, second tap B, third tap starts over.
4. **Cruising speed** - slider, hull's displacement speed to top speed, default the record's cruise speed, live label.
5. Outputs: **Route**, **Distance** nm, **Trip time** h min, **Fuel burned** L and gal, **Tank on arrival** % with a bar, red below the 10% reserve, **Fits in range** Yes or No with the range at that speed.
6. Basis line always visible: curve used and the manufacturer figure it is fitted to.
7. **NOT shown:** fuel on board slider, preset counts, a link to a NautiX page.

**Done when** two taps on the map produce all six outputs and no number on the module is a usage count.

### 13. Ask Waylo {color="blue_bg"}

Per Listing Page Guest: input, four suggested questions, 5 a day unlogged, 20 logged, then the contact prompt. Position after NautiX. The mobile **Ask Waylo** pill anchors here.

### 14. Price and Value {color="blue_bg"}

1. Eyebrow **Is the price fair**. H2 **[Year Brand Model] Price and Value**.
2. Six cards: **Age**, **Engine**, **Options and features**, **Warranty**, **Price history**, **Other market factors**. Copy per Listing Page Guest Price and Value Factors; Price history from the record.
3. Hidden price: cards render without any price figure.

### 15. Finance and Insure This Boat {color="green_bg"}

1. Eyebrow **Can I afford it**. H2 **Finance and Insure This Boat**.
2. Calculator card: **Price** numeric, pre-filled · **Down payment %** numeric, default 10 · **Term** dropdown 10, 15, 20 years, default 20 · **Rate %** numeric, default from EasyFund. Result updates live.
3. Result card: **Est. monthly payment** · **Down payment** dropdown 10, 15, 20, 25 or more · **Credit range** dropdown Excellent 740+, Good 670 to 739, Fair 580 to 669, Not sure · line *"Boat, price and engines are already filled from this listing. Takes less than a minute. Direct bank rates, no markup. No credit impact."*
4. **Get pre-qualified for this boat** - opens `/easy-fund/get-prequalified-internal-vessel/[listingId]/` with make, model, year, engines, horsepower and price prefilled. Never routes through `/boat-loans/`. `cta_location` listing_loan_calculator; the price card and contact card estimates carry listing_price_card and listing_contact_card.
5. Insurance card, equal weight: H3 **Insure this [Brand Model]**, copy per Listing Page Guest, **Get an insurance estimate** to MasterCover with the hull prefilled, `cta_location` listing_insurance.
6. Whole section **NOT shown** for price under 50,000, vessel over 30 years old, PWC, CAD or AUD. Then the price card and contact card estimates are **NOT shown** either.
7. **PLEASE NOTE:** insurance copy says *connects* and *matches*. Never places, quotes, sells, binds, compares.

**Done when** G5 closes and a listing under 50,000 renders no estimate anywhere on the page.

### 16. Video Review {color="blue_bg"}

1. Only where a YachtWay Spotlight exists for the model. Otherwise **NOT shown**.
2. Eyebrow **YachtWay Spotlight**. H2 **[Brand Model] Video Review**. One card, **Watch the [Brand Model] video review**, to `/brands/[brand]-yachts-for-sale/[model]/video-review/`.
3. No YouTube rail. No `VideoObject` on this page for the review.

### 17. Seller {color="blue_bg"}

1. Card: logo or initial, **Seller name**, **Authorized Dealer** or **Factory Direct** where applicable, location, description with **Read more**.
2. Facts: **Listings** [n] of this brand · [n] total · **Authorized dealer of** brand list · **Member since** · **Offices**. **NOT shown:** response rate, response time.
3. **Visit seller profile** to `/dealers/[seller]/`. **Contact seller** scrolls to the contact block on desktop, opens the Request info modal on mobile.
4. Offices per Listing Page Guest Seller's Offices, Dealers and Brokerage Firms only.

### 18. Events, other listings, PDF, FAQ, pillar link {color="blue_bg"}

1. **Events for This Boat** - live stream and in person cards per Listing Page Guest. **NOT shown** with no current or future event.
2. **Other [Seller] Listings** - the seller's own active listings, excluding this one. Six cards, one anchor per card, Year Make Model, whole card clickable, price, city and badge outside the anchor. **All [n] [Seller] listings** to `/dealers/[seller]/`. **NOT shown:** a model page banner, listings from any other seller, similar vessels. Section **NOT shown** when the seller has one listing.
3. **Download the PDF for this [Year Brand Model]** · **Download PDF** per Listing Page Guest.
4. **Frequently Asked Questions** - one H3 per question, answers from the record, `FAQPage` only where visible and complete. Whether listings carry a FAQ is open.
5. **All [noun] for sale** - noun from `nounForm`, destination by length.

**Done when** G4 closes and every card in Other [Seller] Listings resolves to a listing owned by the same seller.

### 19. Internal link contract {color="orange_bg"}

1. Up: the breadcrumb only. Sideways: the location anchor on the meta line, the brand anchor in the description, the video review card, the seller profile from the Seller module and the Other listings anchor. Down: nothing; this is the leaf.
2. Every internal href is relative. Filter and sort combinations are never links. One link text per destination.
3. Seller name is plain text on the contact card and on every card; the seller profile is linked from the Seller module only.

**Done when** the page links to exactly one seller profile and zero `/search/` or filtered URLs.

### 20. Page states {color="orange_bg"}

<table fit-page-width="true" header-row="true">
<tr><td>State</td><td>Behaviour</td></tr>
<tr><td>Price hidden</td><td>Price on application in the price card, bottom bar and meta description. No drop line, no estimate, no price in the message, no Price alert, `Offer` without `price`</td></tr>
<tr><td>New</td><td>No engine hours on the meta line, stat strip or meta description. Condition card reads New</td></tr>
<tr><td>No 3D tour, video or deck layout</td><td>Tile and Deck Layout section absent, grid collapses</td></tr>
<tr><td>No Spotlight</td><td>Video Review absent</td></tr>
<tr><td>No events</td><td>Events absent</td></tr>
<tr><td>Calculator hidden</td><td>Financing section, price card estimate and contact card estimate absent</td></tr>
<tr><td>Seller with one listing</td><td>Other [Seller] Listings absent</td></tr>
<tr><td>Sold</td><td>Per the row: breadcrumb, basic specs, See other [Brand Model] banner, matched active listings, sold date and last asking price. No contact, 3D tour, video or active `Offer`</td></tr>
</table>

### 21. Design system {color="purple"}

@yachtway/ui inside `ShadcnRoot`: **Button** primary and secondary, small, pill for icon buttons · **Badge** for status and chips · **Tabs** for specifications and the unit toggle · **Input** and **Textarea** for the forms · **Card** · **Breadcrumb**. Poppins headlines, Figtree text. Import `@yachtway/ui/styles.css` only where `@yachtway/design-system` is present. The prototype mirrors these in CSS; the build replaces the mirrors.

### 22. Performance and analytics {color="blue_bg"}

1. Core Web Vitals on mobile are a release requirement. Payload budget set for the listing; the `__NEXT_DATA__` fix lands with the re-path, not after. Gallery cover eager, everything below lazy. Map library loads when the NautiX module enters the viewport.
2. Amplitude project 748126. Every new event registered in the tracking plan before release. Autocapture on the listing path.
3. New events: gallery opened, 3D tour opened, video played, spec tab opened, unit toggled, NautiX chip tapped, NautiX slider changed, See all media, section reached at 25, 50, 75, 100 percent scroll.
4. `listing_id` on EF Prequal Submitted and EF Application Submitted. `listing_page` flag on Listing saved and Listing shared. Revive or remove price_alert_created, listing_pdf_downloaded, image_gallery_viewed.

**Done when** field Core Web Vitals pass on mobile and each new event is a distinct registered event.

## Build order

<table fit-page-width="true" header-row="true">
<tr><td>#</td><td>Story</td><td>Section</td></tr>
<tr><td>1</td><td>Internal ID minted in the re-path, `/vessels/` 301s, nested route</td><td>1</td></tr>
<tr><td>2</td><td>Breadcrumb, H1, title, meta description, meta line from the record, server rendered</td><td>1, 3</td></tr>
<tr><td>3</td><td>JSON-LD `Product`, `Offer`, `BreadcrumbList` with blank guards. Hidden price and sold variants</td><td>1, 20</td></tr>
<tr><td>4</td><td>Gallery hero with the 3D tour tile and See all media</td><td>4</td></tr>
<tr><td>5</td><td>Full width sticky nav with Save, Share, Price alert</td><td>5</td></tr>
<tr><td>6</td><td>Two column layout, contact block sticky right</td><td>7</td></tr>
<tr><td>7</td><td>Price card with drop, struck previous price and estimate anchor. Condition card. Four-stat strip</td><td>6</td></tr>
<tr><td>8</td><td>Contact block: phone reveal, WhatsApp, Request info, Schedule a tour</td><td>7</td></tr>
<tr><td>9</td><td>Mobile bottom bar and Ask Waylo pill</td><td>7, 13</td></tr>
<tr><td>10</td><td>About with ownership strip and Read more</td><td>8</td></tr>
<tr><td>11</td><td>Features grid with Show all</td><td>9</td></tr>
<tr><td>12</td><td>Specification tabs, all panels in the DOM, Vessel name in General</td><td>10</td></tr>
<tr><td>13</td><td>Unit toggle, per visitor, applied page wide, visible on Measurements and Tanks</td><td>10</td></tr>
<tr><td>14</td><td>Deck Layout module</td><td>11</td></tr>
<tr><td>15</td><td>NautiX module per the NautiX row, chips from usage data without counts</td><td>12</td></tr>
<tr><td>16</td><td>Ask Waylo module</td><td>13</td></tr>
<tr><td>17</td><td>Price and Value with price history</td><td>14</td></tr>
<tr><td>18</td><td>Loan calculator, deep link pre-qualification with `listing_id`, hide rules</td><td>15</td></tr>
<tr><td>19</td><td>Insurance card with MasterCover prefill</td><td>15</td></tr>
<tr><td>20</td><td>Video Review card where a Spotlight exists</td><td>16</td></tr>
<tr><td>21</td><td>Seller module without response metrics</td><td>17</td></tr>
<tr><td>22</td><td>Events module</td><td>18</td></tr>
<tr><td>23</td><td>Other [Seller] Listings rail and dealer profile anchor</td><td>18</td></tr>
<tr><td>24</td><td>Download PDF, FAQ, pillar anchor</td><td>18</td></tr>
<tr><td>25</td><td>Every conditional module absent when its condition fails</td><td>2, 20</td></tr>
<tr><td>26</td><td>Analytics events registered and firing, autocapture on the listing path</td><td>22</td></tr>
<tr><td>27</td><td>Payload budget and Core Web Vitals gate</td><td>22</td></tr>
<tr><td>28</td><td>@yachtway/ui components replace the prototype CSS</td><td>21</td></tr>
</table>

## Decisions locked

<table fit-page-width="true" header-row="true">
<tr><td>Decision</td><td>Date</td></tr>
<tr><td>Sold pages stay live at the same URL, index follow, contact, video and 3D tour stripped, see other module is the core</td><td>25 Aug</td></tr>
<tr><td>Breadcrumb Home › Brands › [Brand] › [Brand Model] › [listing], same string in the visible crumb and JSON-LD</td><td>29 Aug</td></tr>
<tr><td>Internal ID, eight Crockford Base32 characters, random, immutable, never the HIN. Lands with the re-path</td><td>2 Sep</td></tr>
<tr><td>Contact block in the first viewport on every device, sticky for the whole page. Phone tapped at median 37 s, Request info at 3.8 min</td><td>7 Sep</td></tr>
<tr><td>Fact block is two cards plus a four-stat strip. Buying facts on the meta line. Duty, tax, warranty, availability under the description</td><td>7 Sep</td></tr>
<tr><td>Specifications before Waylo, NautiX before Value, Financing after Value. Waylo used at median 6.1 min</td><td>7 Sep</td></tr>
<tr><td>No similar vessels from other sellers, no model page banner on an active listing. Dealers do not accept competitor inventory on their page</td><td>7 Sep</td></tr>
<tr><td>No response rate, response time or dealer label on the contact card. No Unlimited requests line. No financing checkbox on Request info</td><td>7 Sep</td></tr>
<tr><td>3D tour in the gallery hero with its own label. Deck layout alone. No media count chips under the gallery</td><td>7 Sep</td></tr>
<tr><td>Gallery full width, sticky nav full width across the page, Save, Share, Price alert in the nav, no Call or Request info there</td><td>7 Sep</td></tr>
<tr><td>Single video review card, no YouTube rail</td><td>7 Sep</td></tr>
<tr><td>NautiX chips from real usage without counts, no fuel slider on the listing, no link out. Cruising speed slider default from the record</td><td>7 Sep</td></tr>
<tr><td>Unit toggle only on Measurements and Tanks, remembered per visitor</td><td>7 Sep</td></tr>
<tr><td>Full name in one field. Message pre-filled with the availability question</td><td>7 Sep</td></tr>
<tr><td>Pre-qualification deep links to the internal vessel flow with the hull prefilled, never via `/boat-loans/`. EasyFund listing entries were 34 of 142</td><td>7 Sep</td></tr>
<tr><td>Styled on @yachtway/ui, Poppins and Figtree</td><td>7 Sep</td></tr>
</table>

## Non-goals

A similar vessels rail or cross seller recommendation · a model page banner on an active listing · usage figures or trip counts other than the listing's own view count · a YouTube rail or `VideoObject` for the review · dealer performance metrics · a fuel on board slider on the listing · a NautiX page link · a dark theme · a filtered catalog URL of its own.

## Open

<table fit-page-width="true" header-row="true">
<tr><td>Question</td><td>Section</td></tr>
<tr><td>Title and meta description pattern confirmed before the re-path, so titles and URLs ship as one crawl event</td><td>1</td></tr>
<tr><td>Ask Waylo after NautiX, or beside the description as a product bet</td><td>13</td></tr>
<tr><td>Duty and warranty chips above the fold, as on the Mobile_layout idea</td><td>3, 8</td></tr>
<tr><td>NautiX before Value, or after insurance as on the Mobile_layout idea</td><td>12</td></tr>
<tr><td>Warranties block with expiry dates</td><td>14</td></tr>
<tr><td>Dealer performance metrics on the listing</td><td>17</td></tr>
<tr><td>Fact rows over 40 ft: guests, crew, refit year, flag, VAT</td><td>6</td></tr>
<tr><td>Price and Value shown at all on a hidden price listing</td><td>14</td></tr>
<tr><td>FAQ on listings at all</td><td>18</td></tr>
<tr><td>Fuel on board slider: removed from the prototype, required on the NautiX row</td><td>12</td></tr>
<tr><td>Event banner under the stats and tour calendar in the bottom bar, from the Mobile_layout idea</td><td>6, 7</td></tr>
<tr><td>Sold pages, three photos or five, on the row</td><td>20</td></tr>
</table>

---

*Written 7 September 2026 from the day's decisions, the prototype at commit a6248a1 and Listing Page · Information Hierarchy. Same shape as the Home Page and Location index requirements. Round one by Heigo on the yachtway-user-stories conventions; BAs finalise.*
