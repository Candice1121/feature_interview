# feature_interview
Problem description:
Goal: generate standard deviation data from pricing input

We are given some pricing data. data example
downalod sample data link https://qsltd.sfo2.digitaloceanspaces.com/interview-sample-data/tf-binance-BTC_ETH-2022-07-21.gz

it's gzipped data,
you can unzip it using this python sample code. (Or you can unzip using any other preferrence language)
```
import gzip
with gzip.open(filename, mode="rt") as f:
    for row in f:
        parsed = json.loads(row.rstrip("\n"))
        # do something with parsed
```

Each row of data looks like this

```
# timestamp_ms_received, side (0=buy, 1=sell), price, quantity, symbol_id, timestamp_ms_server_event]
[1669334399012,0,0.072514,0.0165,603,1669334398951]
```
For our task purpose, you can only care about timestamp_ms_received and price, ignore other fields

The task is to write a function to process the file, and generate a set of data to store standard deviation every 10 seconds.
Please note the requirements:
 * each row should contain standard deviation for the last 10 seconds
 * standard deviation is calcalted from pricing data
 * each row should have 1 seconds time gap
 * your function should be able to read from the input .gz file, and output a csv file
 * the output should be written in csv format
 * you should consider your code efficiency, and make sure your code is as fast as possible

the output csv data should looks like this. You need to save output data in a csv file.
```
timestamp, std
1669334400000, 0.124
1669334410000, 1.215
1669334420000, 0.851
1669334430000, 0.566
1669334440000, 1.666
```

Deliverable result:
Please create a github repository, upload your executable code along with output csv in the repo.
