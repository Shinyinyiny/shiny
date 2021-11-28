**複製檔案或目錄**<br>
* 指令：cp -參數  來源檔案   目標檔案<br>
* 參數:<br>
-a：相當於-pdr 的意思<br>
-d：若來源檔為連結檔的屬性(link file)，則複製連結檔屬性而非檔案本身<br>
-i：如果要複製過去的位置已經有相同檔案，會在覆蓋前詢問是否持續進行<br>
-p：將檔案本身屬性(權限、所有者、時間)同時複製過去(一般用於備份居多)<br>
-r：針對目錄下檔案做遞歸複製(整個目錄下每一個檔案複製到你想要的位置)<br>
-s：複製成符號連結檔(symbolic link)(複製成捷徑檔)<br><br><br>

**壓縮檔案**<br>
* 為什麼要壓縮檔案呢？<br>
1. 備份資料的時候，方便整理。<br>
2. 將檔案變小，節省電腦硬碟的空間。(但圖片、音訊、視訊等多媒體檔案壓縮率低，並不能有效節省空間)<br>
3. 將無數個散亂的檔案打包成一個較小的檔案，亦方便資訊在網路上流通。(可將永久免費版之付費軟體輕鬆分享)<br>
4. 壓縮檔案時，可以視情況進行加密。<br><br><br>

**各壓縮的差別**<br>
* 考慮的因素<br>
  * 壓縮率（compression ratio），能夠將檔案壓到多小。<br>
  * 解壓縮所需的時間，也就是需要的 CPU 計算量。<br>
  * 解壓縮所需的記憶體空間。<br>
  * 相容性（compatibility），即解壓縮程式的普遍性，是不是大部分人都有辦法解壓縮這種格式？<br><br><br>

在不同壓縮級別下，壓縮同一文件後的大小:<br>
![image](https://user-images.githubusercontent.com/91866984/143729520-1a86e505-5176-4ccc-9aca-d63d8efdec5e.png)<br><br><br>
在不同壓縮級別下，壓縮同一文件用的時間對比：<br>
![image](https://user-images.githubusercontent.com/91866984/143729532-80e1795e-16f3-4af9-90e6-7c6d08f8f712.png)<br><br><br>
在不同壓縮級別下，解壓同一文件用的時間對比：<br>
![image](https://user-images.githubusercontent.com/91866984/143729566-21ba7d25-5920-4246-97e4-aca301a2cced.png)<br><br><br>

* 在記憶體很小的機器（如小於 128MB）上解壓縮時，則選擇 gzip 格式。<br>
* 在很簡單、沒有什麼工具可用的機器解壓縮時，則選擇 gzip 格式。<br>
* 節省網路頻寬、縮短下載所需要的時間時，則選擇 xz 格式。<br>
* 有最好的壓縮率時，則選擇 tar.xz  格式。<br><br><br>
  
* gzip<br>
  * 壓縮: gzip FileName<br>
  * 解壓縮: <br>
    gunzip FileName.gz<br>
    gzip -d FileName.gz<br>
* xz<br>
  * 壓縮: xz -z FileName<br>
  * 解壓縮: xz -d FileName.xz<br>
* tar.gz<br>
  * 壓縮：tar -zcvf FileName.tar.gz DirName<br>
  * 解壓縮：tar -zxvf FileName.tar.gz<br><br><br>

**檔案搜尋**<br>
* find[path][option][action]filename<br>
  * option<br>
    * -size EX: 找出大於500M的檔案→ -size +500M<br>
    * -name EX：找出為照片的檔案→ -name "*.jpg"<br>
    * -type EX：-type f→ 一般檔案;  -type d→ 一般目錄<br>
    * -user EX：同時找兩個擁有者的檔案<br>
      →-user user1 -o -user user2<br>
  * action -exec<br>
    * ls<br>
    * print<br>
  * which filename
    * -a：系統會顯示所有被找到的命令執行檔之完整路徑<br>
    * -n<文件名長度>指定文件名長度，指定的長度必須大於或等於所有文件中最長的文件名。<br>
    * -p<文件名長度>與-n参數相同，但此處的<文件名長度>包括了文件的路徑。<br>
    * -w：指定輸出欄位的寬度。<br>
    * -V：顯示版本訊息。<br><br><br>
    
**檔案內容查閱**<br>
  * cat: 從第一行顯示檔案內容、形成新檔案<br>
    * cat -n file1 > file2→把file1的檔案內容加上行號後輸入file2檔案<br>
-n  → 由1開始對所有輸出的行數編號
>    → 將多個文件覆蓋到目標文件中
>>  → 將多個文件追加到目標文件中，不覆蓋
tac  從最後一行開始顯示
tac -r -s 'x\|[^x]' test.log→一個接著一個字符的反轉一個文件
-r→將分隔符作為基礎正規表達是處理
-s→使用String作為分隔符代替默認的換行符![image](https://user-images.githubusercontent.com/91866984/143729880-7c3909f2-e5d0-45e8-8ff1-f92f7492af20.png)



