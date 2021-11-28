**『線上升級』機制**<br>
透過此機制，原版光碟只有在第一次安裝時要用到，其他時候只要有網路，便可取得原開發廠商提供的任何軟體。<br><br><br>

**檔案系統目錄結構**<br>
![image](https://user-images.githubusercontent.com/91866984/143556100-09381f3b-fc97-4407-aaad-91e14e92a5df.png)<br><br><br>

**Linux各個目錄存放的內容**<br>
* /：根目錄，所有檔案皆從根目錄開始，只有root使用者具該目錄的許可權<br>
* /root：該目錄為系統管理員，也稱作超級許可權者的使用者主目錄<br>
* /bin：存放經常使用的命令<br>
* /boot：系統啟動時必須讀取的檔案, 包括系統核心<br>
* /home：存放普通使用者的家目錄，每個使用者都有<br>
* /etc：放置與系統設定、管理相關的檔案<br>
* /usr：一個非常重要的目錄，使用者的應用程式和檔案都放在這，類似windows下的program files目錄<br>
* /media：可用來做為光碟、軟碟片、隨身碟與其他分割區的自動掛載點<br>
* /tmp：供全部使用者暫時放置檔案的目錄<br>
* /var：系統執行時, 內容經常變動的資料或暫存檔(log file), 都會放置在這個目錄裡<br><br><br>

**檔案命名原則**
* 區分英文字元的大小寫，基本以小寫為主<br>
* 檔名長度**至多256個字元**，可包括字母、數字、"."(點)、"_"(下劃線)和"-"(連字元)<br>
* 檔名不可使用的字元："?"(問號),"*"(星號), " "(空格), "$"(貨幣符), "&", "("擴號, "/" (斜線), ".."<br>
* .filename，檔名前面有小數點，為隱藏檔<br><br><br>

**Linux指令-絕對/相對路徑的移動**<br>
* 絕對路徑：路徑的寫法『一定由根目錄 / 寫起』，<br>
例如： /usr/share/doc 這個目錄。<br>
* 相對路徑：路徑的寫法『不是由 / 寫起』，<br>
例如由 /usr/share/doc 要到 /usr/share/man 底下時，寫成： 『cd ../man』，相對路徑意指『相對於目前工作目錄的路徑！』<br><br><br>

**比較特殊的目錄**<br>
* 『.』 ：代表此層目錄<br>
* 『..』：代表上一層目錄<br>
* 『-』 ：代表前一個工作目錄<br>
* 『~』 ：代表『目前使用者身分』所在的家目錄<br><br><br>

|指令|功能&用途|
|---|---------|
|cd|變換目錄|
|pwd|顯示目前目錄所在位置|
|is|顯示目錄下所有檔案|
|touch|建立檔案|
|cp|複製|
|cat|查看檔案內容|
|vi|編輯檔案|
|mkdir|建立一個新目錄|
|mkdir -p|同時建立多個目錄|
|rmdir|刪除一個裡面是空的空目錄|
|rm|刪除檔案|
|rm -r|強制刪除|
|mv|移動 重新命名|<br><br><br>

**使用者與群組**<br>
* 關於身分:<br>
   * 身分分類<br>
     * user(owner)<br>
     * group<br>
     * other<br>
   * 群組(group)的主要用意<br>
     * 將帳號歸類，有助於類似專案開發<br>
     * 每個使用者均可加入多個群組<br>
* 關於身分類別:<br>
   * 系統管理員:root<br>
   * 一般帳號:<br>
     * 系統帳號(用於系統帳號的工作)<br>
     * 一般使用者帳號(用於一般使用者登入用)<br><br><br>

**查看檔案目錄資訊**<br>
* ls -l：顯示目錄下的所有檔案詳細資訊<br>
* ls -al：顯示目錄下的所有檔案(包含隱藏檔)詳細資訊<br>
![image](https://user-images.githubusercontent.com/91866984/143727735-1f5288a9-b766-48af-92b1-89d4d46ca34a.png)<br><br><br>

**更改檔案或目錄全限**<br>
* chown可修改檔案或目錄的擁有者及群組<br>
![image](https://user-images.githubusercontent.com/91866984/143727813-921989bb-5b4b-4f43-ad77-545b73277567.png)<br><br><br>

**更改使用者權限**<br>
* chmod可控制檔案如何被他人調用→ chmod [-cfvR] [--help] [--version] mode file…<br>
* mode許可權設定字串→ [ugoa...][[+-=][rwxX]...][,...]<br>
![Untitled](https://user-images.githubusercontent.com/91866984/143728563-f2686609-cf20-4bad-89e4-2a260feff205.png)<br><br><br>

**目錄權限**<br>
* chmod 664 test.txt<br>
![Untitled1](https://user-images.githubusercontent.com/91866984/143728649-961f698a-9f50-43ab-8dfd-265c927e5b6a.png)<br><br><br>
![image](https://user-images.githubusercontent.com/91866984/143728572-f693591e-9386-4999-b54d-7217d98c871e.png)<br><br><br>

**更改使用者權限**<br>
* 檔案file1.txt設為所有人接可讀取:<br>
  * chmod ugo+r file1.txt<br>
* 將檔案file1.txt 與 file2.txt file2.txt設為該檔案用有者，與其所屬同一群體者可寫入，但其他以外的人則不可寫入:<br>
  * chmod ug+w,o-w file1.txt file2.txt<br>
* 將 ex1.py 設定為只有該檔案擁有者可以執行:
  * chmod u+x ex1.py<br>
* 將目前目錄下的所有檔案與子目錄皆設為任何人可讀取:<br>
  * chmod -R a+r*<br>
* chmod a=rwx file == chmod 777 file<br>
* chmod ug=rwx,o=x file == chmod 771 file<br><br><br>

**編輯文檔**<br>
* nano<br>
  * Ctrl C: 顯示游標所在<br>
  * Ctrl W: 查詢命令，按下後會跳轉到末行的反白位置，輸入要查詢的內容再按enter即可。<br>
![image](https://user-images.githubusercontent.com/91866984/143728976-a2ca334b-baa1-490a-82b4-50b395d52e36.png)<br><be><br>
* vi/vim(vim相當於vi的升級版)<br>
  * 一般模式: 一般模式：可使用上下左右進行游標宜動、刪除字元及複製貼上檔案資料。<br>
  * 編輯模式：編輯文字<br>
![image](https://user-images.githubusercontent.com/91866984/143729054-d505d0fb-5e94-4102-8c7a-57d47bb41779.png)<br>
  (i鍵即可進入編輯模式)<br>
![image](https://user-images.githubusercontent.com/91866984/143729057-026ab28f-7c3d-491c-9c57-eeac3849d0d8.png)<br>
  (Esc鍵退出編輯模式)<br>
  * 命令列模式<br>
  ![Untitled2](https://user-images.githubusercontent.com/91866984/143729177-4ccfef0b-51e6-4491-80c9-b5cdc972092a.png)<br><br><br>
            
