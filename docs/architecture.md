# System Architecture

## 1. Overview

The Hospitality Sales & Revenue Intelligence Platform uses Google BigQuery as its centralized analytical data source.

The application separates data retrieval from business calculations. BigQuery supplies the required aggregated data, while dedicated TypeScript calculation modules process business metrics and reporting logic.

The application accesses BigQuery through a server-side, read-only integration.

## 2. High-Level Architecture

```text
                 Business Users
                       |
                       v
             Interactive Dashboard
                       |
             Global Filters & Views
                       |
                       v
             Application Data Layer
                       |
              Server-Side Integration
                       |
                       v
                Google BigQuery
                       |
        --------------------------------
        |              |               |
        v              v               v
     Bookings       Inventory       Sales Data
        |              |               |
        --------------------------------
                       |
                       v
              Aggregated Data Results
                       |
                       v
             TypeScript Calculation Layer
                       |
        --------------------------------
        |              |               |
        v              v               v
     KPIs          Comparisons       Reports
        |              |               |
        --------------------------------
                       |
                       v
             Dashboard Visualizations
                       |
                       v
               CSV / Excel Export
```

## 3. Data Source

Google BigQuery is the platform's single analytical data source.

The data model covers:

- Booking information
- Cancelled bookings
- Property room inventory
- Room master information
- Booking channel classifications
- Monthly revenue and occupancy targets
- Additional revenue transactions
- Website enquiries
- Financial-year sales lead trackers

The application no longer relies on its previous Google Sheets data connection.

## 4. Data Access Layer

BigQuery queries are executed server-side through a dedicated integration module.

Key characteristics:

- Read-only data access
- Server-side query execution
- A maximum query processing limit of 1 GB per query
- No direct browser-side access to BigQuery credentials

The server-side boundary helps keep database access separate from the client-facing dashboard.

## 5. Business Logic Layer

Business calculations are maintained in separate TypeScript modules.

The calculation layer includes dedicated logic for:

- Overview metrics
- Target calculations
- Lead metrics
- Booking metrics
- Property performance

Examples of calculation modules include:

- `overview-calc.ts`
- `targets-calc.ts`
- `leads-calc.ts`
- `bookings-calc.ts`

These calculation files are designed as pure, tested logic modules.

BigQuery supplies the aggregated rows required by the calculation layer.

## 6. Dashboard Layer

The dashboard presents processed information through multiple business modules:

- Overview
- Performance
- Booking Details
- Lead Tracker
- OTA
- Reports

Global filters are shared across the application. Filter selections are reflected in the URL so that users can navigate between pages while retaining the selected context.

## 7. Reporting Layer

The reporting functionality supports:

- Consolidated property reports
- Folio-level reports
- Company-level booking reports
- CSV exports
- Browser-generated Excel exports

## 8. Design Principles

The architecture follows these principles:

1. Centralized analytical data source.
2. Server-side database access.
3. Separation of data retrieval and business calculations.
4. Reusable calculation logic.
5. Shared filtering across dashboard pages.
6. Exportable business reports.
7. Separation of sensitive configuration from public-facing code.

## 9. Security Considerations

The public portfolio version does not expose:

- BigQuery project identifiers
- Private dataset and table identifiers
- Credentials or API keys
- Guest personal information
- Private business records

The architecture description is intentionally anonymized.
