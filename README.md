#  TML Blocks - SafeGraph Competitor & Consumer Behavior

Uncover ground-level competitor and consumer insights with SafeGraph & ThoughtSpot. 

SafeGraph builds datasets for physical places, powering analytics covering business listings, building footprints, and aggregated foot traffic data for millions of points of interest (POI) and thousands of brands in the US and Canada. Using ThoughtSpot, you can immediately ask location-based questions leveraging the whole breadth and depth of Safegraph data. 

The SafeGraph TML Blocks provide out-of-the-box templates to help get started analyzing SafeGraph data on ThoughtSpot. Analyze your store performance with granular details into foot traffic and consumer behavior insights. Additionally, idenify competitors and track how changing market and brand trends impact your store locations. 

# Artifacts 

## Worksheets
- SafeGraph Competitor & Consumer Behavior

## Liveboards
- Industry Overview
- Competitor Insights
- Consumer Behavior Insights


# Implementation Steps

**Prequestites:** The TML blocks require the following products from SafeGraph: Places, Spend, and Patterns. 

Once you have downloaded the Zip file and have verified its contents, the implementation steps are as follows:

### 1. Explode JSON Columns
SafeGraph Core and Patterns datasets contain JSON columns. JSON columns are rich in information, but they need to be exploded to play well in SQL. Use the examples sql in "SAFEGRAPH - JSON COLUMN EXPLODE.sql" to explode these JSON columns, so that each key-value pair becomes its own row.

Feel free to explode additional JSON columns to add fields of interest. The following is the tables which are used in this template: 
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
| pg_user_vw | None |
| stl_alert_event_log_vw |  <img width="500" alt="Screen Shot 2022-03-31 at 2 05 25 PM" src="https://user-images.githubusercontent.com/102629468/161161164-f619ccb5-903d-493b-962d-ae49d048cf15.png">|
| stl_ddltext_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 09 52 PM" src="https://user-images.githubusercontent.com/102629468/161161198-9151e011-0146-41cd-9c25-42d959f5f600.png"> |
| stl_load_errors_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 02 PM" src="https://user-images.githubusercontent.com/102629468/161161218-ec8b4169-66b3-4a4e-b586-bf29427b6406.png"> |
| stl_plan_info_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 11 PM" src="https://user-images.githubusercontent.com/102629468/161161235-8f79cb01-4211-442a-ad97-959dcaf9c96a.png"> |
| stl_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 22 PM" src="https://user-images.githubusercontent.com/102629468/161161260-fee0a62b-1cee-442a-bee4-5fc19191d775.png"> |
| stl_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 28 PM" src="https://user-images.githubusercontent.com/102629468/161161269-ed815212-420a-42bb-bcf3-c464c8091690.png"> |
| stl_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 39 PM" src="https://user-images.githubusercontent.com/102629468/161161281-b50d7692-06f4-4133-a608-5576fa1274e4.png"> |
| stl_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 45 PM" src="https://user-images.githubusercontent.com/102629468/161161297-6440fa1e-abee-4154-a0e4-b9dc5214f5e6.png"> |
| stl_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 10 53 PM" src="https://user-images.githubusercontent.com/102629468/161161322-5b7b22c3-b5d6-4bf0-93c4-38ea7f3b518a.png"> |
| stl_wlm_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 11 01 PM" src="https://user-images.githubusercontent.com/102629468/161161341-c3879d20-ac52-487e-b45f-ddde6b23df50.png"> |
| stl_wlm_query_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 11 11 PM" src="https://user-images.githubusercontent.com/102629468/161161347-42d41083-51e2-424e-a187-ddc0dab74bea.png"> |
| stv_node_storage_capacity_vw | None |
| stv_recents_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 11 21 PM" src="https://user-images.githubusercontent.com/102629468/161161437-ab8b1bb2-11db-4acc-b38b-e0f29c3f9e72.png"> |
| stv_sessions_vw | <img width="500" alt="Screen Shot 2022-03-31 at 2 11 28 PM" src="https://user-images.githubusercontent.com/102629468/161161447-5cebfffb-a27f-4c0e-ad4d-c9a8aca1a5b8.png"> |

4. Import the TML for the worksheets and verify that it has all been imported without any errors.
5. Import the TML for the pinboard and verify that it has all been imported without any errors.
6. You are ready to start searching your Redshift data!
