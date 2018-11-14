# ADT104137 - midterm
## 1.
* **設定 ver 變數，內容為『 my kernel version is 3.xx 』，其中 3.xx 為 uname -r 輸出的資訊，並顯示出ver變數的值。(10%)**

<pre><code># ver="my kernel version is $(uname -r)"
# echo $ver</code></pre>

* **請顯示目前PATH環境變數的值為何，並說明PATH的功用為何? (10%)**


## 2.
* **有一個檔案的屬性權限為 drwxrwsr-x 3 root mail 4096 2月 16 2017 mail/，請說明此檔案的特性。(10%)**

此檔案(mail)為目錄檔，並且擁有者(root)及所屬群組(mail)有全部(讀取、修改、執行)的權限，而非以上兩者的其餘用戶只有讀取及執行的權限。此外設有SGID，讓執行者在執行過程中能獲得該程式群組權限。檔案連結數為3，檔案容量有4GB，於2017/2/16最後修改此檔案。

* **假設有一個script.sh檔案的權限為-rw-r--r--，若希望讓所有人可以執行該檔案，請問該如何下達指令？請使用數字法與符號法各操作一次。(10%)**

數字法
<pre><code># chmod +1 script.sh</code></pre>
符號法
<pre><code># chmod +x script.sh</code></pre>



## 3.
* **說明實體連結與符號連結的差異。(10%)**

實體連結(hard link)設定連結檔時，磁碟空間及inode的數目都不會變，且若將連結相同inode的檔名之中任一刪除，其inode和block都還是存在的，可透過另一檔名讀取到正確的檔案資料。<br/>

符號連結(symbolic link)則是再建立一個獨立的檔案，所以inode及磁碟空間會與連結檔不相同，且來源檔若是被刪除，使用此連結方式的檔案會開不了。

* **在家目錄下建立一個檔名為 hosts.real 的實體連結指到 /etc/hosts？ (請用相對路徑表示家目錄) (5%)**

<pre><code># ln /etc/hosts ~/hosts.real</code></pre>

* **在家目錄下建立一個檔名為 hosts.symbo 的符號連結指到 /etc/hosts？ (請用相對路徑表示家目錄 (5%)**

<pre><code># ln -s /etc/hosts ~/hosts.symbo</code></pre>
