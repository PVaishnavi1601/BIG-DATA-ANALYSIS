# BIG-DATA-ANALYSIS
Perform analysis on a large dataset using tools like PYSPARK or DASK to demonstrate scalability

**COMPANY:** CODTECH IT SOLUTIONS

**MAME:** P VAISHNAVI

**INTERN ID:** CT08DH1432

**DOMAIN:** Data Analytics

**DURATION:** 8 WEEKS

**MENTOR:** NEELA SANTOSH

Task Description:
For the first task of my internship, I performed large-scale data analysis using PySpark to demonstrate the scalability of big data processing. I worked with the New York City Yellow Taxi trip dataset, which contained millions of records. My goal was to clean, transform, and analyze the dataset to extract actionable insights, such as peak travel hours, popular passenger counts, and average fares.

To complete the task, I made extensive use of YouTube tutorials for practical demonstrations of PySpark operations, environment setup, and optimization techniques. These visual explanations helped me understand how Spark sessions work, how to efficiently load and clean large datasets, and how to apply transformations like filtering, grouping, and aggregations. Additionally, I referred to quickref.me for concise PySpark syntax references, function usage, and examples. This quick-access documentation allowed me to quickly recall command structures and avoid common syntax errors during implementation.

By following this approach, I learned how to handle large datasets that would otherwise be too slow to process using standard Python libraries like Pandas. I also gained hands-on experience in using Spark SQL functions, working with Parquet files, and writing analysis results to CSV for reporting. The task improved my ability to combine online learning resources effectively — YouTube for conceptual clarity and quickref.me for rapid syntax lookup — enabling me to complete the analysis efficiently. Overall, this experience enhanced both my technical skills in distributed data processing and my problem-solving abilities when working with real-world big data projects.

Output:
Requirement already satisfied: pyspark in /usr/local/lib/python3.11/dist-packages (3.5.1)
Requirement already satisfied: py4j==0.10.9.7 in /usr/local/lib/python3.11/dist-packages (from pyspark) (0.10.9.7)
Schema of dataset:
root
 |-- VendorID: long (nullable = true)
 |-- tpep_pickup_datetime: timestamp_ntz (nullable = true)
 |-- tpep_dropoff_datetime: timestamp_ntz (nullable = true)
 |-- passenger_count: double (nullable = true)
 |-- trip_distance: double (nullable = true)
 |-- RatecodeID: double (nullable = true)
 |-- store_and_fwd_flag: string (nullable = true)
 |-- PULocationID: long (nullable = true)
 |-- DOLocationID: long (nullable = true)
 |-- payment_type: long (nullable = true)
 |-- fare_amount: double (nullable = true)
 |-- extra: double (nullable = true)
 |-- mta_tax: double (nullable = true)
 |-- tip_amount: double (nullable = true)
 |-- tolls_amount: double (nullable = true)
 |-- improvement_surcharge: double (nullable = true)
 |-- total_amount: double (nullable = true)
 |-- congestion_surcharge: double (nullable = true)
 |-- airport_fee: double (nullable = true)

First 5 rows:
+--------+--------------------+---------------------+---------------+-------------+----------+------------------+------------+------------+------------+-----------+-----+-------+----------+------------+---------------------+------------+--------------------+-----------+
|VendorID|tpep_pickup_datetime|tpep_dropoff_datetime|passenger_count|trip_distance|RatecodeID|store_and_fwd_flag|PULocationID|DOLocationID|payment_type|fare_amount|extra|mta_tax|tip_amount|tolls_amount|improvement_surcharge|total_amount|congestion_surcharge|airport_fee|
+--------+--------------------+---------------------+---------------+-------------+----------+------------------+------------+------------+------------+-----------+-----+-------+----------+------------+---------------------+------------+--------------------+-----------+
|       1| 2021-01-01 00:30:10|  2021-01-01 00:36:12|            1.0|          2.1|       1.0|                 N|         142|          43|           2|        8.0|  3.0|    0.5|       0.0|         0.0|                  0.3|        11.8|                 2.5|       NULL|
|       1| 2021-01-01 00:51:20|  2021-01-01 00:52:19|            1.0|          0.2|       1.0|                 N|         238|         151|           2|        3.0|  0.5|    0.5|       0.0|         0.0|                  0.3|         4.3|                 0.0|       NULL|
|       1| 2021-01-01 00:43:30|  2021-01-01 01:11:06|            1.0|         14.7|       1.0|                 N|         132|         165|           1|       42.0|  0.5|    0.5|      8.65|         0.0|                  0.3|       51.95|                 0.0|       NULL|
|       1| 2021-01-01 00:15:48|  2021-01-01 00:31:01|            0.0|         10.6|       1.0|                 N|         138|         132|           1|       29.0|  0.5|    0.5|      6.05|         0.0|                  0.3|       36.35|                 0.0|       NULL|
|       2| 2021-01-01 00:31:49|  2021-01-01 00:48:21|            1.0|         4.94|       1.0|                 N|          68|          33|           1|       16.5|  0.5|    0.5|      4.06|         0.0|                  0.3|       24.36|                 2.5|       NULL|
+--------+--------------------+---------------------+---------------+-------------+----------+------------------+------------+------------+------------+-----------+-----+-------+----------+------------+---------------------+------------+--------------------+-----------+
only showing top 5 rows

Total records: 1369769
Top Passenger Counts:
+---------------+------+
|passenger_count| count|
+---------------+------+
|            1.0|944508|
|            2.0|159975|
|            3.0| 43587|
|            5.0| 30853|
|            0.0| 26255|
|            6.0| 25153|
|            4.0| 16164|
|            7.0|     3|
|            8.0|     1|
+---------------+------+

Average Trip Distance:
+----------------------+
|Average_Distance_Miles|
+----------------------+
|     2.739080255980912|
+----------------------+

Peak Pickup Hours:
+-----------+------+
|pickup_hour| count|
+-----------+------+
|         15|104195|
|         14|102947|
|         16| 98231|
|         17| 97076|
|         13| 94345|
|         12| 88969|
|         18| 88582|
|         11| 80635|
|         10| 74185|
|          9| 67070|
|         19| 66316|
|          8| 62263|
|         20| 45008|
|          7| 40613|
|         21| 35080|
|         22| 29010|
|          6| 21288|
|         23| 17557|
|          0| 11035|
|          1|  7198|
+-----------+------+
only showing top 20 rows

Average Fare per Passenger Count:
+---------------+------------------+
|passenger_count|          Avg_Fare|
+---------------+------------------+
|            0.0|16.295573795463728|
|            1.0|16.364253050389625|
|            2.0|17.045421159547328|
|            3.0| 16.81395645490984|
|            4.0| 17.22453662459553|
|            5.0|16.549825624732783|
|            6.0|16.218310340711426|
|            7.0|            101.71|
|            8.0|              16.3|
+---------------+------------------+
