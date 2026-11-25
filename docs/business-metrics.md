# Business Metrics and KPI Definitions

## 1. Overview

This document describes the key hospitality and sales metrics presented in the dashboard.

Metric calculations are handled by dedicated TypeScript calculation modules. The definitions below explain the business meaning of each metric; exact implementation details should be verified against the application source code.

## 2. Revenue Metrics

### Revenue

The monetary value generated from applicable booking and stay records within the selected reporting period.

### Room Nights Sold

The number of room nights sold during the selected stay period.

This metric is based on stay-date information rather than reservation creation date.

### Average Daily Rate (ADR)

Measures the average room revenue earned per sold room night.

**Conceptual formula:**

ADR = Room Revenue / Room Nights Sold

### Revenue per Available Room (RevPAR)

Measures room revenue relative to available room nights.

**Conceptual formula:**

RevPAR = Room Revenue / Available Room Nights

## 3. Occupancy Metrics

### Occupancy

Measures the percentage of available room nights that were sold.

**Conceptual formula:**

Occupancy (%) = (Room Nights Sold / Available Room Nights) × 100

Available room nights depend on the property inventory and reporting period.

## 4. Target Metrics

### Revenue Target Achievement

Compares actual revenue against the assigned revenue target.

**Conceptual formula:**

Revenue Achievement (%) = (Actual Revenue / Revenue Target) × 100

### Occupancy Target

Compares actual occupancy with the monthly occupancy target.

### ADR Target

Compares actual ADR with the assigned monthly ADR target.

### Prorated Targets

For selected date ranges, monthly targets are adjusted to the relevant reporting period.

The dashboard supports prorated target comparisons for revenue and occupancy, and ADR target comparisons where applicable.

A RevPAR target is not available in the supplied target data.

## 5. Booking Metrics

### Booking Count

Measures the number of booking records within the selected reservation-date period.

### Cancellation Metrics

Measures cancelled booking activity using reservation-date context.

### Repeat Guests

Identifies repeat-guest activity within the booking analysis.

The exact repeat-guest matching logic should be confirmed from the application implementation before publishing a technical definition.

### Booking Channel Mix

Groups booking activity into standardized categories:

- B2B
- B2C
- OTA

This allows channel-level comparisons and contribution analysis.

## 6. Sales Lead Metrics

The Lead Tracker provides visibility into:

- Total recorded leads
- Leads by source
- Leads by property
- Leads by stage
- Leads by owner
- Lost leads
- Financial-year comparisons

The dashboard supports sales pipeline monitoring across financial years.

Specific lead conversion formulas should be documented only after validating the application's stage definitions and calculation logic.

## 7. Performance Comparisons

The dashboard supports comparison against a previous reporting period.

Comparison views help users understand changes in key metrics such as:

- Revenue
- Room nights
- Occupancy
- ADR
- RevPAR

The selected date range and comparison period determine the reporting context.

## 8. Reporting Metrics

Consolidated reports aggregate daily property-level information.

ADR and occupancy are recomputed from aggregated totals rather than simply averaging individual property or daily percentages.

This approach helps ensure that consolidated metrics reflect the underlying revenue, room-night, and availability totals.

## 9. Important Interpretation Notes

- Reservation date and stay date represent different business events.
- Booking metrics and stay metrics should use the appropriate date context.
- ADR should be interpreted in relation to sold room nights.
- RevPAR should be interpreted in relation to available room nights.
- Occupancy requires a reliable room inventory denominator.
- Target comparisons should account for the selected reporting period.
- Consolidated ratios should be recomputed from their underlying totals where appropriate.

## 10. Calculation Ownership

Business calculations are maintained in separate TypeScript calculation modules.

Examples include:

- Overview calculations
- Target calculations
- Lead calculations
- Booking calculations

These modules are designed as pure, tested calculation logic, separate from the BigQuery data retrieval layer.
