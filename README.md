# Data Warehouse Mappings

This repository contains the mappings used for loading dimensions in a data warehouse environment. The mappings involve both Slowly Changing Dimension (SCD) Type 1 and Type 2 processes. Below are the details for each mapping.

## m_load_dim_channels
- **Source Table:** `CHANNELS`
- **Target Table:** `DIM_CHANNELS`
- **Action:** Update/Insert
- **Mapping Type:** SCD Type 1
- **Transformations:**
  - **Connected Lookup:** Checks whether the record exists in the target.
  - **Expression:** Compares new and existing records to identify changes.
  - **Filter 1:** Processes only new records.
  - **Filter 2:** Processes only existing records.
  - **Update Strategy 1:** Inserts new records into the target table.
  - **Update Strategy 2:** Updates existing records in the target table.
  - **Sequence Generator:** Generates the primary key for new records.

## m_load_dim_countries
- **Source Table:** `COUNTRIES`
- **Target Table:** `DIM_COUNTRIES`
- **Action:** Update/Insert
- **Mapping Type:** SCD Type 1
- **Transformations:**
  - **Connected Lookup:** Checks whether the record exists in the target.
  - **Expression:** Compares new and existing records to identify changes.
  - **Filter 1:** Processes only new records.
  - **Filter 2:** Processes only existing records.
  - **Update Strategy 1:** Inserts new records into the target table.
  - **Update Strategy 2:** Updates existing records in the target table.
  - **Sequence Generator:** Generates the primary key for new records.

## m_load_dim_promotions
- **Source Table:** `PROMOTIONS`
- **Target Table:** `DIM_PROMOTIONS`
- **Action:** Update/Insert
- **Mapping Type:** SCD Type 1
- **Transformations:**
  - **Connected Lookup:** Checks whether the record exists in the target.
  - **Expression:** Compares new and existing records to identify changes.
  - **Filter 1:** Processes only new records.
  - **Filter 2:** Processes only existing records.
  - **Update Strategy 1:** Inserts new records into the target table.
  - **Update Strategy 2:** Updates existing records in the target table.
  - **Sequence Generator:** Generates the primary key for new records.

## m_load_dim_products
- **Source Table:** `PRODUCTS`
- **Target Table:** `DIM_PRODUCTS`
- **Action:** Update/Insert
- **Mapping Type:** SCD Type 2
- **Transformations:**
  - **Connected Lookup:** Checks whether the record exists in the target.
  - **Expression:** Compares new and existing records to identify changes.
  - **Filter 1:** Processes only new records.
  - **Filter 2:** Processes only existing records.
  - **Update Strategy 1:** Inserts new records into the target table.
  - **Update Strategy 2:** Inserts existing records into the target table.
  - **Update Strategy 3:** Updates the effective end date for existing records.
  - **Sequence Generator:** Generates the primary key for new records.
  - **Expression 1:** Uniquely assigns a primary key for new records.
  - **Expression 2:** Uniquely assigns a primary key for existing records.

---

### Notes
- The mappings for `CHANNELS`, `COUNTRIES`, and `PROMOTIONS` follow the SCD Type 1 approach, where only the current state of data is retained.
- The `PRODUCTS` mapping follows the SCD Type 2 approach, where historical data is preserved by keeping track of changes to records over time.
