# Div_Arb
See if this dividend arb thing is legit

###1. Raw Data Processing
The initial data was send from Emily using her access to UT data (we can look into getting more). The data has all expiry/strike price data for ~4.3k tickers. The data is 24gb zipped (140gb raw) and you can download it from my datalake using command `gsutil cp gs://ucf-data/options-consolidated/options_consolidated.csv.gz .`

Initially the data is sorted by year then by ticker. In order to partition into seperate files for each ticker first unzip the file use the following command in terminal (make an Options folder before you do so)
`awk -F, 'NR==1 {h=$0; next} {f="Options/"$28".csv"} !($28 in p) {p[$28]; print h > f} {print >> f; close(f)}' FILE_NAME.csv`

###2. Accessing the data
The tickers will be located in the `ucf-data` bucket under the path `gs://ucf-data/options/`. To look at the stocks that you can use the following command `gsutil ls gs://ucf-data/options/`. I will also be adding a notebook that will be able to work as a wrapper and access and filter data from google cloud according to our needs.

###3. 
