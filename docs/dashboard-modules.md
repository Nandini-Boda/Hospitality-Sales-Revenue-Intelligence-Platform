# Dashboard Modules

## Overview

The Hospitality Sales & Revenue Intelligence Platform contains six primary navigation modules, with additional reporting submodules.

The dashboard is designed to provide a centralized view of commercial performance across multiple hospitality properties.

## 1. Overview

**Route:** `/`

The home page presents a consolidated view of business performance.

### Key Features

- Total revenue
- Room nights sold
- Occupancy
- Average Daily Rate (ADR)
- Revenue per Available Room (RevPAR)
- Comparison against a previous reporting period
- Revenue trend charts
- Occupancy trend charts
- Booking channel mix
- Property-wise performance
- Monthly target versus actual performance

### Business Purpose

Provides a high-level snapshot of hospitality business performance and helps management identify changes in revenue, occupancy, and commercial results.

## 2. Performance

**Route:** `/performance`

Presents property-level performance using the core overview metrics.

### Key Features

- Revenue by property
- Occupancy by property
- ADR by property
- RevPAR by property
- Monthly target comparisons
- Target prorating for the selected date range

RevPAR targets are not displayed because a corresponding target is not available in the supplied target data.

### Business Purpose

Supports property comparisons and helps identify locations performing above or below expectations.

## 3. Booking Details

**Route:** `/bookings`

Provides booking-level analytical views.

### Key Features

- Booking KPIs
- Guest-related booking metrics
- Repeat-guest metrics
- Cancellation metrics
- Room nights sold
- Sold inventory analysis
- Website booking enquiries
- Booking channel breakdown

### Date Logic

Different metrics use different date contexts:

- Booking and cancellation metrics are based on reservation date.
- Room nights and inventory analysis are based on stay date.
- Stay-related calculations distinguish past and future dates relative to the current date.

### Business Purpose

Helps understand booking activity, cancellations, demand patterns, and booking channel contribution.

## 4. Lead Tracker

**Route:** `/leads`

Provides a sales lead management and analytical view across financial years.

### Key Features

- Separate financial-year tabs
- Lead date
- Source
- Property
- Format
- Sales stage
- Total
- Lead owner
- Lead metrics
- Lost-lead tracking

### Business Purpose

Helps sales teams monitor pipeline activity, identify lead sources, review stage progression, and understand lost opportunities.

## 5. OTA Analytics

**Route:** `/ota`

Provides a dedicated view of online travel agency channel performance.

### Business Purpose

Helps users examine OTA-related commercial activity and understand the contribution of online travel channels.

Detailed OTA metrics should be documented after reviewing the actual page implementation.

## 6. Reports

**Route:** `/reports`

The reporting section contains three submodules.

### 6.1 Consolidated Report

**Route:** `/reports/consolidated`

Features:

- Daily property-level reporting
- Financial-year quarter grouping
- ADR recomputed from aggregated totals
- Occupancy recomputed from aggregated totals
- CSV export

### 6.2 Folio Report

**Route:** `/reports/folio`

Features:

- Folio-level financial matrix
- Booking-related revenue reporting
- Additional transaction reporting
- CSV export

F&B revenue is not populated from this dashboard's supplied BigQuery data source because a corresponding F&B sales table is not available in that dataset.

### 6.3 Company Report

**Route:** `/reports/company`

Features:

- Company-level booking analysis
- Live and historical booking information
- One row per property and folio
- Revenue reporting

## 7. Shared Dashboard Functionality

### Global Filters

The application provides shared filters in the dashboard header.

- Date range selection
- Financial-year selection
- Property selection
- Comparison-period selection

### URL-Based Filter Persistence

Selected filters are reflected in the URL.

This allows filter selections to remain consistent while navigating between pages and enables users to share links with the selected reporting context.

### Data Export

Supported report pages provide:

- CSV downloads
- Browser-generated Excel exports

## 8. Navigation Summary

| Module | Route |
|---|---|
| Overview | `/` |
| Performance | `/performance` |
| Booking Details | `/bookings` |
| Lead Tracker | `/leads` |
| OTA | `/ota` |
| Reports | `/reports` |
| Consolidated Report | `/reports/consolidated` |
| Folio Report | `/reports/folio` |
| Company Report | `/reports/company` |

## 9. Access Behavior

The current application does not require user login. The `/login` route redirects to the home page.

This describes the current application behavior, not a recommendation to expose private business data publicly.
