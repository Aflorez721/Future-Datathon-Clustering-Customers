# Future-Datathon-Clustering-Customers
Cluster Big Bazaar customers based on their shopping and other data given.

### About the data.
* **Missing Values**: Not too many missing values. The DOB, Gender, State, PinCode, promotion_description and PaymentUsed fields have missing values.
* **Data Quality**: Wrong Pincodes, multiple spellings for same state name. 

### Data Preprocessing.
* Imputing missing values: 
 * Missing DOB imputed by ‘1/1/1970’.
 * Missing States imputed by new missing category ‘missing_state’.
 * Missing Gender by third value ‘2’.
* Cleaning data:
 * Multiple states were with different spellings for same state like ‘MADHYA PRADESH’ and ‘MP’. One name given to these like ‘MADHYA PRADESH’ to both above.
* One hot encoding:
 * States: All states one hot encoded.
 * discountUsed: All 6 types of discounts one hot encoded.
 * tillNo: All 25 till numbers one hot encoded.

### Feature Engineering.
* Age: Age of the customer till 2017.
* Age_on_transaction_date: Age of customer on date of transaction.
* Promo_used: Binary variable showing if a promocode was used.

### Clustering Approach.
After data preprocessing and feature engineering the dataset has following features:
* customerID
* DOB
* Gender
* State
* PinCode
* transactionDate
* store_code
* store_description
* till_no
* transaction_number_by_till
* promo_code
* promotion_description
* product_code
* product_description
* sale_price_after_promo
* discountUsed
* age
* age_on_transaction_date
* promo_used
* ANDHRA PRADESH
* ASSAM
* BIHAR
* CHANDIGARH
* CHATTISGARH
* DELHI
* DUMMY
* GOA
* GUJARAT
* HARYANA
* HIMACHAL PRADESH
* JAMMU AND KASHMIR
* JHARKHAND
* KARNATAKA
* KERALA
* MADHYA PRADESH
* MAHARASHTRA
* MANIPUR
* ORISSA
* Other
* PUNJAB
* RAJASTHAN
* SIKKIM
* TAMIL NADU
* TRIPURA
* UTTAR PRADESH
* UTTARANCHAL
* WEST BENGAL
* missing_state
* x
* till_1
* till_2
* till_3
* till_4
* till_5
* till_6
* till_7
* till_8
* till_9
* till_10
* till_11
* till_12
* till_13
* till_14
* till_15
* till_16
* till_17
* till_18
* till_19
* till_20
* till_21
* till_22
* till_23
* till_24
* till_25
* BBProfitClub
* BBSavingsClub
* FGShoppingFest
* FuturePrivilegeClub
* Payback
* T24Club

### Algorithm:
K Means is used for clustering customers based on most of the features stated above. Clustering is done on store basis and on scaled data. K is decided by training silhouette score individually for each store.

### Behaviour of clusters:
Since there are different number of clusters for different stores so each of them have different behavior.
The most influential features in clusters appear to be Gender, sales_price_after_promo, age, age_on_transaction_date, state and the type of discount used by the customer.

Let’s see for store 4843:
There are 5 clusters for this store. Since there are lot of features based on which clustering is done so it’s not possible to plot the centroids of clusters, but here I give the centroid interpretations of 5 clusters for this store.

|CentroidNum|Gender|Sale_price_after_promo|Age|Promo_used|BBProfitClub|BBSavingsClub|FGShoppingFest|FuturePrivelegeClub|Payback|T24Club|
|--:|--:|--:|--:|---|---|---|---|---|---|---|
| 1  | 0.859  | 122  |41   |0.3   |0.07   |0.03   |0.03   |0.003   |0.9   |0.3   |
| 2 |  0.893 |517   |39   |0.55   |0.06   |0.04   |0.01   |0.01   |0.9   |0.3   |
|  3 |  1 |267   |34   |0.4   |0.2   |0   |0   |0   |1   |0.4   |
|  4 |  1 | 155  |31   |0.6   | 0  | 0  | 0.1  | 0  | 0.9  | 0.1  |
|  5 |  1 | 99  |51   |1   | 0  | 0  | 0  | 0  | 1  | 0  |

**Observations**:
* Cluster 1, 2 have some female customers, rest have all male customers.
* Cluster 2 has rich customers, while cluster 5 has poorest :P Just joking, this may be based on their requirements and not their wealth.
* Cluster 4, 5 customers use promo code more than other three clusters.
* Cluster 3, 4 have younger customers as compared to other clusters.
* All cluster customers predominantly use Payback as discount type. Weird?? May be not because for other stores the situation is pretty different.

Let’s also take store 2615 for comparison:
There are 4 clusters for this store.

|CentroidNum|Gender|Sale_price_after_promo|Age|Promo_used|BBProfitClub|BBSavingsClub|FGShoppingFest|FuturePrivelegeClub|Payback|T24Club|
|--:|--:|--:|--:|---|---|---|---|---|---|---|
| 1  | 0.857  | 148  |43  |0.41   |0.58  |0.16   |0.06   |0.001   |0.42   |0.08   |
| 2 |  0.911 |484   |41   |0.66   |0.3   |0.3   |0.06   |0   |0.45   |0.08   |
|  3 |  1 |379   |54      |0.5   |0.5   |0.5   |0   |0   |0   |0   |
|  4 |  1 |459  |42       |0.33   | 0.67  | 0  | 0  | 0  | 0.3  | 0  |

Observations:
* Cluster 1, 2 have some female customers, rest have all male customers.
* Not much variation in age.
* Only customers of cluster 2 seem to use promocode.
* Here we can see difference from store 4843 with respect to discount type used. Here cluster 1, 4 use BBProfitClub discount type, cluster 2 uses Payback mostly while also sometime use BBProfitClub and BBSavingsClub. 


So, the customers can be clustered based on prices of products, promos available on those products. Age and gender are also influential features in clustering.

Major libraries used:
* Sklearn
* Pandas
* Numpy
* Datetime

