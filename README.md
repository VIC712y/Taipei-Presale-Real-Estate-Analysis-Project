## Data Scraping from Actual Price Registration and Storing into SQLite (Jan 2011 to Jun 2024)  
### 實價登錄爬蟲及SQLite資料庫儲存 (民國110年至113年6月)


In this section, we aim to collect data from Taiwan's official *Actual Price Registration* platform, focusing on presale real estate transactions in Taipei City. The data spans from January 2011 to June 2024, covering over a decade of market trends.

目標是從台灣官方的*實價登錄*平台收集資料，重點放在台北市的預售房地產交易。數據範圍涵蓋從2011年1月至2024年6月，覆蓋超過十年的市場趨勢。
  
  
- **Web Scraping:** A Python-based Scrapy framework is used to automate the extraction of transaction data from the *Actual Price Registration* website. The focus is on presale transactions.  
  **網頁爬蟲：** 使用基於Python的Scrapy框架來自動提取*實價登錄*網站上的交易資料，重點放在預售交易。  
  - Collected fields: property type, district, price, area, number of rooms, and transaction date.  
    收集欄位：房屋類型、區域、價格、面積、房間數以及交易日期。  
  - Data saved in an SQLite database for ease of access and future analysis.  
  - 將數據儲存於SQLite資料庫中，便於後續訪問和分析。  
  
- **Challenges:**  
  - Handling changes in the website’s structure over the years.  
  - 處理多年來網站結構的變化。  
  - Filtering only relevant presale transactions from the larger pool of real estate data.
  - 從大量房地產資料中篩選出相關的預售交易。  


![Scrapy](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/Scrapy.png?raw=true)  
  
![Scrapy2](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/Scrapy2.png?raw=true)  
  
![sql](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/sql.png?raw=true)  

  
## Data Cleaning and Geocoding Using TGOS (WGS84 Coordinate System)  
### 將資料清洗後轉移至內政部以導出座標系統 (WGS84)   


Once the raw data is collected, it's necessary to clean and standardize it, particularly focusing on the property addresses.   
The *Taiwan Geographic Information System* (TGOS) is used to convert these addresses into geospatial coordinates (WGS84 format), allowing for spatial analysis.

當收集到原始資料後，必須進行清理和標準化，特別是針對房屋地址。使用*台灣地理資訊系統* (TGOS)將這些地址轉換為地理座標（WGS84格式），以進行空間分析。

- **Address Standardization:** Cleaning and formatting addresses to ensure consistency. This may involve:  
  **地址標準化：** 清理並格式化地址以確保一致性。這可能包括：  
    
  - Removing extra spaces and characters.  
    移除多餘的空格和字符。
  - Converting traditional Chinese formats to a consistent layout.  
    將傳統中文格式轉換為一致的格式。
  
  
- **Geocoding:** Using the TGOS API to map the cleaned addresses to precise geographic coordinates (latitude and longitude).  
  **地理編碼：** 使用TGOS API將清理後的地址映射到精確的地理座標（經緯度）。  
  - Storing these coordinates alongside the original data in the SQLite database.  
    將這些座標與原始資料一起儲存於SQLite資料庫中。  
  
- **Challenges:**  
  - Some addresses may not match perfectly due to variations in spelling or format.  
    由於拼寫或格式的變化，一些地址可能無法完美匹配。 
  - Ensuring high accuracy in the geocoding process.  
    確保地理編碼過程中的高準確性。 


![TGOS](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/TGOS.png?raw=true)

---
Creating Initial Insights with a Dashboard (Tableau)  
用數位儀表板建置洞悉報告
===


With clean and geocoded data, we now focus on generating meaningful insights through visualizations. A digital dashboard (likely built using Python libraries like Dash or Plotly) allows stakeholders to explore key trends interactively.

通過清理和地理編碼的數據，我們現在專注於通過可視化產生有意義的洞察報告。數位儀表板（可能使用Dash或Plotly等Python庫建置）允許利害關係人以互動方式探索關鍵趨勢。

#### Key Visualizations:  

- **Price Heatmaps:** Displaying property prices across different districts of Taipei, with variations by transaction date and area.  
  **價格熱圖：** 顯示台北市不同區域的房地產價格，隨著交易日期和面積的變化而變動。

- **Time-Series Analysis:** Showing trends in presale prices over time, revealing market peaks and declines.  
  **時間序列分析：** 顯示預售價格隨時間變化的趨勢，揭示市場高峰和低谷。

- **Scatter Plots:** Visualizing the relationship between price, area, and geographic location (coordinates).  
  **散點圖：** 可視化價格、面積與地理位置（座標）之間的關係。

#### Key Metrics:  

- Median price per square meter by district.  
  每個區域的每坪中位價格。
    
- Price trends over time.  
  隨著時間的價格趨勢。  
  
- Popular districts for presale properties.  
  預售房地產熱門區域。
#### Challenges:  

  
- Designing a user-friendly interface that allows for interaction with data filters (e.g., by date range, district).  
  設計用戶友好的界面，允許與數據篩選器（例如按日期範圍、區域）進行互動。

![dashboard](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/dashboard.png?raw=true)  

https://public.tableau.com/app/profile/victor.yuan/viz/TP_17104211156880/1?publish=yes
---

## Machine Learning for Predictive Analysis
### 進行機器學習模型預測
  
The next step is to leverage machine learning to predict future trends in the presale real estate market. The focus is on building models that can forecast property prices based on historical data, location, and property features.  
接下來的步驟是利用機器學習來預測預售房地產市場的未來趨勢。重點是構建可以根據歷史數據、地理位置和房產特徵來預測房價的模型。

#### Steps:  
#### 步驟:
- **Feature Selection:** Using important features such as transaction date, property size, number of rooms, and geographic coordinates to train the model.  
  **特徵選擇：** 使用重要的特徵，如交易日期、房產面積、房間數和地理座標來訓練模型。
![dashboard](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/scatterplot.png?raw=true)  
- **Model Training:** A *RandomForestRegressor* model could be a good choice for this task, given its ability to handle non-linear relationships and interactions between features.  
  **模型訓練：** *隨機森林迴歸模型* 可能是這項任務的良好選擇，因為它能夠處理特徵之間的非線性關係和交互作用。  
  Target variable: property price.  
  目標變數：房價。 
  
![dashboard](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/non-linear-relationships.png?raw=true)  
- **Model Evaluation:** Use metrics like Mean Absolute Error (MAE) or Root Mean Squared Error (RMSE) to assess the model's accuracy.  
  **模型評估：** 使用平均絕對誤差 (MAE) 或均方根誤差 (RMSE) 等指標來評估模型的準確性。

#### Challenges:  
#### 挑戰:
- Handling the imbalanced distribution of property prices across different regions.
  處理不同區域房價分佈不均的問題。
- Dealing with outliers and missing data in the dataset.
  處理數據集中異常值和缺失值。
