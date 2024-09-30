### By Scraping Data from Taiwan's Official Platform, Focusing on Presale Real Estate Transactions in Taipei City

**目標：** 從台灣官方的*實價登錄*平台收集資料，重點放在台北市的預售房地產交易。數據範圍涵蓋從2011年1月至2024年6月，涵蓋超過十年的市場趨勢。

---

1. **Web Scraping (網頁爬蟲)**  
   - A Python-based Scrapy framework is used to automate the extraction of transaction data from the *Actual Price Registration* website. Focus is on presale transactions.  
   - **網頁爬蟲：** 使用基於Python的Scrapy框架來自動提取*實價登錄*網站上的交易資料，重點放在預售交易。  
   - **Collected fields:** property type, district, price, area, number of rooms, transaction date.  
     **收集欄位：** 房屋類型、區域、價格、面積、房間數、交易日期。  
   - **Data saved in SQLite database** for ease of access and future analysis.  
     **將數據儲存於SQLite資料庫**中，便於後續訪問和分析。  
   - ![Scrapy](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/Scrapy.png?raw=true)  
     ![Scrapy2](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/Scrapy2.png?raw=true)  
     ![sql](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/sql.png?raw=true)  

2. **Challenges (挑戰)**  
   - **Handling changes** in the website’s structure over the years.  
     **處理多年來網站結構的變化。**  
   - **Filtering** only relevant presale transactions from the larger pool of real estate data.  
     **從大量房地產資料中篩選出相關的預售交易。**

---

### Data Cleaning and Geocoding Using TGOS (WGS84 Coordinate System)

**資料清理與地理編碼：** 使用台灣地理資訊系統 (TGOS) 將地址轉換為WGS84格式，進行空間分析。

1. **Address Standardization (地址標準化)**  
   - **Cleaning and formatting addresses** to ensure consistency.  
     **清理並格式化地址**以確保一致性。  
   - Removing extra spaces and characters.  
     **移除多餘的空格和字符。**  
   - Converting traditional Chinese formats to a consistent layout.  
     **將傳統中文格式轉換為一致格式。**  

2. **Geocoding (地理編碼)**  
   - Using the TGOS API to convert addresses into geographic coordinates (latitude, longitude).  
     **使用TGOS API將地址轉換為地理座標（經緯度）。**  
   - Storing coordinates in SQLite database.  
     **將座標儲存於SQLite資料庫中。**  
   - ![TGOS](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/TGOS.png?raw=true)

---

### Creating Initial Insights with a Dashboard (Tableau)  
**數位儀表板建置洞察報告**  
Using Tableau to visualize key trends in presale real estate transactions.

1. **Key Visualizations (關鍵可視化):**  
   - **Price Heatmaps:** Displaying property prices across districts of Taipei.  
     **價格熱圖：** 顯示台北市不同區域的房價變動。  
   - **Time-Series Analysis:** Showing trends in presale prices over time.  
     **時間序列分析：** 顯示預售價格的時間趨勢。  
   - **Scatter Plots:** Visualizing the relationship between price, area, and location.  
     **散點圖：** 可視化價格、面積和地理位置的關係。  

2. **Key Metrics (關鍵指標):**  
   - Median price per square meter by district.  
     **各區域的每坪中位價格。**  
   - Price trends over time.  
     **隨著時間的價格趨勢。**  
   - Popular districts for presale properties.  
     **熱門的預售房地產區域。**  
   - ![dashboard](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/dashboard.png?raw=true)  
   - [Dashboard Link](https://public.tableau.com/app/profile/victor.yuan/viz/TP_17104211156880/1?publish=yes)

---

### Machine Learning for Predictive Analysis  
**機器學習預測分析**

1. **Feature Selection (特徵選擇):**  
   - Using features like transaction date, property size, rooms, and geographic coordinates.  
     **使用交易日期、房產面積、房間數和地理座標作為特徵。**  

2. **Model Training (模型訓練):**  
   - Using RandomForestRegressor to predict property prices.  
     **使用隨機森林迴歸模型來預測房價。**  
   - ![dashboard](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/scatterplot.png?raw=true)  
   - ![non-linear](https://github.com/VIC712y/Taipei-Presale-Real-Estate-Analysis-Project/blob/main/Pic/non-linear-relationships.png?raw=true)  

3. **Model Evaluation (模型評估):**  
   - Using Mean Absolute Error (MAE) or Root Mean Squared Error (RMSE).  
     **使用MAE或RMSE評估模型。**

4. **Challenges (挑戰):**  
   - Handling the imbalanced distribution of property prices.  
     **處理房價分佈不均的問題。**  
   - Dealing with outliers and missing data.  
     **處理異常值和缺失值。**
