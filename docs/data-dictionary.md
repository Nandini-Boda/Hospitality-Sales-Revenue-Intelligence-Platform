# Data Dictionary

## 1. Overview

This document describes the anonymized logical data entities used by the Hospitality Sales & Revenue Intelligence Platform.

The original application uses Google BigQuery as its centralized data source. The names below are portfolio-friendly logical names and are not the original production table identifiers.

## 2. Booking Data

### Booking Fact

**Purpose:** Stores booking and stay-related information used for revenue, occupancy, booking, and reporting analysis.

| Logical field | Description |
|---|---|
| Stay date | Date associated with the guest stay |
| Reservation date | Date when the booking was created |
| Arrival date | Guest arrival date |
| Departure date | Guest departure date |
| Folio reference | Booking or folio reference |
| Property | Property associated with the booking |
| Room | Room category or type |
| Room reference | Room identifier |
| Booking channel | Source through which the booking originated |
| Guest count | Number of guests |
| Night count | Number of nights |
| Daily revenue | Revenue associated with the booking date |
| Booking status | Current booking status |

Guest contact information is intentionally excluded from this public data dictionary.

### Cancelled Booking Fact

**Purpose:** Supports cancellation analysis and historical booking comparisons.

Contains booking-related information associated with cancelled reservations.

## 3. Property and Inventory Data

### Property Inventory

**Purpose:** Stores available room inventory by property.

| Logical field | Description |
|---|---|
| Property | Property identifier |
| Available room count | Number of available inventory keys |

### Room Master

**Purpose:** Provides room-level inventory information.

| Logical field | Description |
|---|---|
| Property | Property identifier |
| Room | Room category |
| Room reference | Room identifier |
| Room count | Number of rooms associated with the record |

## 4. Booking Channel Data

### Channel Mapping

**Purpose:** Maps booking sources into standardized business channel categories.

| Logical field | Description |
|---|---|
| Booking source | Original booking source |
| Channel category | Standardized classification |

Channel categories include:

- B2B
- B2C
- OTA

The mapping supports consistent channel-level reporting.

## 5. Sales Target Data

### Monthly Targets

**Purpose:** Stores monthly commercial targets by property.

| Logical field | Description |
|---|---|
| Target month | Month associated with the target |
| Property | Property identifier |
| Revenue target | Monthly revenue target |
| Occupancy target | Monthly occupancy target |
| ADR target | Monthly Average Daily Rate target |

The target data supports actual-versus-target analysis and date-range prorating.

## 6. Additional Revenue Data

### Transaction Fact

**Purpose:** Stores additional revenue transaction information used in extra revenue, folio, and company reporting.

The public documentation does not expose original transaction identifiers or private financial records.

## 7. Website Enquiry Data

### Website Enquiry Fact

**Purpose:** Supports analysis of enquiries received through the booking website.

Logical attributes include:

- Enquiry received date
- Enquiry message
- Enquiry source context

Names and mobile numbers are excluded from this public documentation.

## 8. Sales Lead Data

### Lead Tracker

**Purpose:** Tracks sales leads across financial years.

| Logical field | Description |
|---|---|
| Lead date | Date the lead was recorded |
| Source | Lead acquisition source |
| Property | Associated property |
| Format | Lead or business format |
| Stage | Current sales pipeline stage |
| Total | Lead value or recorded total |
| Owner | Responsible lead owner |

Separate financial-year datasets support year-wise lead tracking.

## 9. Entity-to-Module Mapping

| Logical entity | Main dashboard usage |
|---|---|
| Booking Fact | Overview, Performance, Booking Details, Reports |
| Cancelled Booking Fact | Booking Details |
| Property Inventory | Overview, Performance, Reports |
| Room Master | Overview, Performance, Reports |
| Channel Mapping | Overview, Performance, Booking Details |
| Monthly Targets | Overview, Performance |
| Transaction Fact | Extra Revenue, Folio, Company Reports |
| Website Enquiry Fact | Booking Details |
| Lead Tracker | Lead Tracker |

## 10. Data Quality and Interpretation Notes

- Booking dates and stay dates serve different analytical purposes.
- Reservation-based metrics should use reservation dates where appropriate.
- Room-night and inventory metrics should use stay dates.
- Channel mappings standardize source classifications.
- Target calculations must account for the selected reporting period.
- Property inventory is required for occupancy and RevPAR calculations.
- Guest contact details must not be exposed in public portfolio materials.

## 11. Scope and Limitations

This document is a logical, anonymized data dictionary.

It does not publish:

- Original BigQuery project or dataset identifiers
- Exact production table names
- Private column-level schemas beyond the necessary logical descriptions
- Credentials or sensitive business records

Exact data types, keys, relationships, and validation rules should be documented from the reviewed application source code before publishing implementation-level details.
