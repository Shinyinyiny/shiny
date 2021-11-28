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
      * -n  → 由1開始對所有輸出的行數編號<br>
      * >   → 將多個文件覆蓋到目標文件中<br>
      * >>  → 將多個文件追加到目標文件中，不覆蓋<br><br><br>
      
  * tac: 從最後一行開始顯示<br>
    * tac -r -s 'x\|[^x]' test.log →一個接著一個字符的反轉一個文件<br>
      * -r →將分隔符作為基礎正規表達是處理<br>
      * -s →使用String作為分隔符代替默認的換行符<br><br><br>
      
  * more 一頁一頁的顯示檔案內容<br>
    * more +20 testfile→從第20行開始顯示testfile的文檔內容<br>
      * ENTER：向下n行(default為1行)<br>
      * Ctrl+F/SPACE：向下滾動一屏<br>
      * Ctrl+B：返回上一屏<br><br><br>
      
  * less 與 more 類似，顯示檔案室允許用戶既可以向前又可以向後翻頁閱讀檔案<br>
    * ps -ef |less→ps查看進程信息並通過less分頁顯示<br>
      * j→下一行<br>
      * k→上一行<br>
      * G→移動到最後一行<br>
      * g→移動到第一行<br><br><br>
      
  * head 取出前面幾行(預設10行)<br>
    * -n：後面接數字，代表幾行的意思<br><br><br>

  * tail 取出後面幾行(預設10行)<br>
    * -n：後面接數字，代表幾行的意思<br>
    * -n +20：只想列出20行以後的資料<br><br><br>

**資料傳輸**<br>
![Untitled3](https://user-images.githubusercontent.com/91866984/143730119-cadd0753-cc06-40dd-b7a0-2b4ffe63c6d3.png)<br><br><br>
![Untitled4](https://user-images.githubusercontent.com/91866984/143730148-3ffb4852-d234-409c-823c-e09dc3a478d8.png)<br><br><br>

* 溝通案例：小美開瀏覽器(客戶端)並輸入Youtube首頁網址(伺服器端)<br>
1. 瀏覽器(客戶端)向YouTube的遠端主機(伺服器端)發出一個請求<br>
2. 該請求透過網路被傳遞到YouTube首頁的位址<br>
3. 位於YouTube首頁的遠端主機(伺服器端)收到一個請求<br>
4. 遠端主機(伺服器端)會根據請求內容，找到一個對應的網路資源<br>
5. 取出對應的網路資源，伺服器將其回傳至小美的瀏覽器<br>
6. 瀏覽器(客戶端)收到回傳內容，開始解析資源，顯示於瀏覽器上<br><br><br>
 
* Port<br>
通訊埠號是 TCP/UDP 與上層通訊的通道。<br>
當 TCP/UDP 要傳送訊息時，會指定要由哪一個通訊埠號來接收。<br>
一些常用的服務會使用特定的埠號來等待要求的訊息。埠號是由 16 個位元所組成的號碼，0 ~ 255 為保留號碼，256 ~ 65535 則可自行設定。<br><br><br>

![Untitled5](https://user-images.githubusercontent.com/91866984/143730284-b3aa07a6-fad1-428c-8c82-688aa1c32a97.png)<br><br><br>

  |Port|Service|Explaination|
  |----|-------|------------|
  |22|ssh|一種加密的網路傳輸協定，可在不安全的網路中及公安全的傳輸環境|
  |23|telnet|一種很傳統的連線程式，可用來診斷各種伺服器與網路連線問題|
  |80|http|超文本傳輸協定|
  |20/21|ftp|一個傳遞客戶端與伺服器之間的命令(21，命令通訊埠);另一個傳遞資料(20，資料通訊埠)|
  |443|https|超級文字傳輸安全協定|
  |25|smtp|簡單郵件傳輸協定，是一個在網際網路上傳輸電子郵件的標準|
  |53|DNS|網域名稱系統，將域名和IP位址相互對應的一個分散式資料庫，能夠使人更方便的存取網際網路|
