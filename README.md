=== Tugas2_PengelolaanBigData ===
Untuk pengerjaan tugas 2 ini melibatkan 2 metode utama yaitu: Proses Crawling Data dan Analisis Data
A. Crawling Data (Menggunakan Google Collab untuk mendapatkan data)

!pip install serpapi
!pip install pandas
!pip install google-search-results

import pandas as pd
from serpapi import GoogleSearch

- Define parameters for the Google Maps API query
params = {
    "engine": "google_maps",
    "q": "McD",
    "ll": "@-6.905977,107.613144,15.1z",
    "type": "search",
    "api_key": "(diisi dengan api key)"
}

- Perform the Google Maps API query
search = GoogleSearch(params)
results = search.get_dict()
local_results = results["local_results"]

- Convert the results to a Pandas DataFrame
df = pd.DataFrame(local_results)

- Rename columns if needed
df = df.rename(columns={
    "name": "Name",
    "address": "Address",
    "phone": "Phone",
    "rating": "Rating"
})
print (df)

- Save the DataFrame to a CSV file
csv_filename = "pizza_places.csv"
df.to_csv(csv_filename, index=False)

B. Mengatur hadoop untuk windows

1. Download hadoop for windows
2. hadoop version untuk melihat versi hadoop
3. hdfs namenode -format :  untuk melakukan format namenode
4. ubah path ke hadoop sbin
5. start-dfs.cmd : untuk menjalankan hdfs
6. jps : untuk melihat apa saja yang running pada hdfs
7. start-yarn.cmd : untuk menjalankan yarn daemons
8. localhost:9870 : berisi localhost dari namenodenya
9. localhost:8088 : berisi cluster pada hadoop

C. Pengecekan pada sql client

1. Masukkan data yang sudah di crawl pada my sql qlient
2. Buka mysql workbench untuk melihat apakah data sudah masuk
3. ganti directory ke hadoop/sqoop/bin
4. sqoop list-databases --connect jdbc:mysql://localhost/ --username sqoop --password localhost : untuk mengubungkan MySQL dengan sqoop


Hadop dengan ekosistem sqoop pada Cloudera 
Langkah-langkah 
1. mysql -u root -pccloudera
2. melihat database
   show databases
   use (database)
   show tables
3. Melihat isi tabel
   select * from (nama tabel)
4. Melakukan import
   sqoop import \ --connect jdbc:mysql://localhost:3306/nama_database \ --username pengguna \ --password sandi \ --table nama_tabel \ --target-dir /lokasi_tujuan_di_HDFS
5. Cek tabel berhasil diimport
   hdfs dfs -fs -R /usercloudera/(nama file)

   
