#  TML Blocks - SafeGraph Competitor & Consumer Behavior

Uncover ground-level competitor and consumer insights with SafeGraph & ThoughtSpot. 

SafeGraph builds datasets for physical places, powering analytics covering business listings, building footprints, and aggregated foot traffic data for millions of points of interest (POI) and thousands of brands in the US and Canada. Using ThoughtSpot, you can immediately ask location-based questions leveraging the whole breadth and depth of Safegraph data. 

The SafeGraph TML Blocks provide out-of-the-box templates to help get started analyzing SafeGraph data on ThoughtSpot. Analyze your store performance with granular details into foot traffic and consumer behavior insights. Additionally, identify competitors and track how changing market and brand trends impact your store locations. 

# Artifacts 

## Worksheets
- SafeGraph Competitor & Consumer Behavior

## Liveboards
- **Industry Overview: Contextualize how overall industry trends impact store performance**

<img width="1728" alt="Screen Shot 2022-08-24 at 5 45 33 PM" src="https://user-images.githubusercontent.com/102629468/186548843-8c77b775-6e4c-4be9-9322-4ef86ac6bc74.png">

- **Competitor Insights: Map the competitive landscape with competitor consumer behavior and sales**

<img width="1728" alt="Screen Shot 2022-08-24 at 5 45 18 PM" src="https://user-images.githubusercontent.com/102629468/186548852-16157ba6-8766-4e0d-9c1d-1b742c4c1b63.png">


- **Consumer Behavior Insights: Determine how many people visit your store, who they are, and what they spend**

<img width="1728" alt="Screen Shot 2022-08-24 at 5 44 55 PM" src="https://user-images.githubusercontent.com/102629468/186548868-fcb49abb-1104-47e6-9f17-10c40954fa4a.png">

# Implementation Steps

**Prequestites:** The TML blocks require the following products from SafeGraph: Places, Spend, and Patterns. 

Once you have downloaded the Zip file and have verified its contents, the implementation steps are as follows:

### 1. Explode JSON Columns
SafeGraph Core and Patterns datasets contain JSON columns. JSON columns are rich in information, but they need to be exploded to play well in SQL. Use the examples sql in "SAFEGRAPH - JSON COLUMN EXPLODE.sql" to explode these JSON columns, so that each key-value pair becomes its own row.

Feel free to explode additional JSON columns to add fields of interest. The following are the tables that are used in this template: 
- BUCKETED_CUSTOMER_FREQUENCY
- BUCKETED_CUSTOMER_INCOMES
- CUSTOMER_HOME_CITY
- DWELL_TIMES
- MEAN_SPEND_PER_CUSTOMER_BY_FREQUENCY
- MEAN_SPEND_PER_CUSTOMER_BY_INCOME
- SPEND_BY_DAY
- SPEND_BY_DAY_OF_WEEK
- TRANSACTION_INTERMEDIARY
- VISITS_BY_DAY

### 2. Log into your ThoughtSpot instance and create an Embrace connection to all of the relevant views.
You should have the following tables available in your ThoughtSpot account:
- CORE_POI 
- CORE_POI_SPEND
- PATTERNS
- BUCKETED_CUSTOMER_FREQUENCY
- BUCKETED_CUSTOMER_INCOMES
- CUSTOMER_HOME_CITY
- DWELL_TIMES
- MEAN_SPEND_PER_CUSTOMER_BY_FREQUENCY
- MEAN_SPEND_PER_CUSTOMER_BY_INCOME
- SPEND_BY_DAY
- SPEND_BY_DAY_OF_WEEK
- TRANSACTION_INTERMEDIARY
- VISITS_BY_DAY


### 3. Create all of the required joins between the views.

| **Name** | **Joins** |
| ----------- | ----------- |
| CUSTOMER_HOME_CITY_to_CORE_POI | <img width="515" alt="Screen Shot 2022-08-24 at 3 34 18 PM" src="https://user-images.githubusercontent.com/102629468/186546716-492f1fc1-16e4-4bde-a225-816a587d26f1.png"> |
| CORE_POI_to_SPEND_BY_DAY | <img width="510" alt="Screen Shot 2022-08-24 at 3 34 44 PM" src="https://user-images.githubusercontent.com/102629468/186545928-e8c1308a-81b9-4e44-ac86-d832e79dc44f.png"> |
| DWELL_TIMES_to_CORE_POI |<img width="520" alt="Screen Shot 2022-08-24 at 3 34 54 PM" src="https://user-images.githubusercontent.com/102629468/186546281-18ace0f2-3935-421c-8fa9-1385f56efc9b.png">|
| VISITS_BY_DAY_to_CORE_POI |<img width="518" alt="Screen Shot 2022-08-24 at 3 35 03 PM" src="https://user-images.githubusercontent.com/102629468/186546293-e65dabd4-0bda-48e2-b24c-2231d466bf78.png">|
| MEAN_SPEND_PER_CUSTOMER_BY_INCOME_to_CORE_POI | <img width="514" alt="Screen Shot 2022-08-24 at 3 35 11 PM" src="https://user-images.githubusercontent.com/102629468/186546300-67821370-6a86-481d-98ee-38a9a2e076a5.png">|
| SPEND_BY_DAY_OF_WEEK_to_CORE_POI |<img width="501" alt="Screen Shot 2022-08-24 at 3 35 19 PM" src="https://user-images.githubusercontent.com/102629468/186546316-15c5718f-765c-485f-918f-075065b58b7d.png">|
| Core_POI to CORE_POI_SPEND | <img width="512" alt="Screen Shot 2022-08-24 at 3 35 33 PM" src="https://user-images.githubusercontent.com/102629468/186546346-17b411dd-8e94-435f-b2fc-e40a23304045.png">|
| CORE_POI_to_PATTERNS | <img width="510" alt="Screen Shot 2022-08-24 at 3 35 40 PM" src="https://user-images.githubusercontent.com/102629468/186546372-ec868404-1653-4dfc-9e5f-267687b04219.png">|
| BUCKETED_CUSTOMER_FREQUENCY_to_CORE_POI | <img width="520" alt="Screen Shot 2022-08-24 at 3 35 27 PM" src="https://user-images.githubusercontent.com/102629468/186546337-ba855f8f-9704-4acf-b0e7-3d3b68e7a9c1.png">|
| BUCKETED_CUSTOMER_INCOMES_to_CORE_POI |<img width="510" alt="Screen Shot 2022-08-24 at 3 34 36 PM" src="https://user-images.githubusercontent.com/102629468/186546496-5ac39c98-4e5d-4565-b1fc-b64544dd7a7a.png">|
| TRANSACTION_INTERMEDIARY_to_CORE_POI | <img width="514" alt="Screen Shot 2022-08-24 at 3 34 24 PM" src="https://user-images.githubusercontent.com/102629468/186546507-cfc4cea5-7cf6-471d-b817-4426ee710ecb.png"> | 

**Schema**: 

<img width="878" alt="Screen Shot 2022-08-24 at 3 34 11 PM" src="https://user-images.githubusercontent.com/102629468/186546543-db69c3fb-7a46-4a76-b564-cace7cf44910.png">


### 4. Import the TML for the worksheets and verify that it has all been imported without any errors.

### 5. Import the TML for the liveboards and verify that it has all been imported without any errors.
  - Edit liveboard filter to analyze relevant competitors and industries. 

### 6. You are ready to start searching your SafeGraph data!


