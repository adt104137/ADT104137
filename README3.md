# ADT104137 - HW3
## 1.
### * 建立帳號名稱分別為 examuser1 ,examuser2 ,examuser3 的用戶，同時為這三個帳戶設定密碼 ItIsExam
<pre><code># useradd examuser1
# passwd examuser1</code></pre>
系統會詢問您想設定的密碼，輸入 IsItExam
<pre><code>New password:IsItExam(看不到)</code></pre>
再次確認密碼
<pre><code>Retype new password:IsItExam(看不到)</code></pre>
![01](pic2/01.PNG)
### * 刪除系統中examuser3的帳號，連同家目錄及郵件檔案同步刪除
<pre><code># userdel -r examuser3</code></pre>
在userdel指令中加入-r，會連同該帳號的家目錄及郵件檔案一同刪除<br/>
輸入id指令查詢
<pre><code># id examuser3</code></pre>
![02](pic2/02.PNG)<br/>
轉換到home下查詢
<pre><code># cd /home
# ls -l</code></pre>
發現已經沒有之前新增的examuser3之目錄<br/>
![03](pic2/03.PNG)
### * 刪除examuser1，但保留其家目錄及郵件檔案
<pre><code># userdel examuser1</code></pre>
刪除examuser1，但沒有在指令中加-r，保留了他的家目錄<br/>
在home中查詢
<pre><code># ls -l</code></pre>
![04](pic2/04.PNG)<br/>
發現其家目錄由UID以及GID替代examuser1為使用者
### * 嘗試以原本的UID及GID重建帳號
建立一群組，給定原使用者的GID作為群組ID
<pre><code># gruopadd -g 1001 examuser1</code></pre>
創建帳號，指定原UID為使用者的ID，並將該使用者加入原群組
<pre><code># useradd -u 1001 -g examuser1 examuser1</code></pre>
查詢使用者的UID及GID
<pre><code># id examuser1</code></pre>
查詢home下的家目錄
<pre><code># ls -l</code></pre>
重新定密碼給examuser1
<pre><code># passwd examuser1</code></pre>
![05](pic2/05.PNG)

## 2.
### * 建立examuser4使用者
<pre><code># useradd examuser4
# passwd examuser4</code></pre>
### * 將/etc/securetty 複製給 examuser4，且該帳號要能夠完整使用該檔案
查看securetty原本的權限
<pre><code># ls -ld /etc/securetty</code></pre>
將securetty複製到examuser4之家目錄下
<pre><code># cp -r /etc/securetty /home/examuser4</code></pre>
轉換到家目錄下
<pre><code># cd /home/examuser4</code></pre>
更改securetty的擁有者以及其權限
<pre><code># chown examuser4 securetty
# chmod 777 securetty</code></pre>
最後確認權限
<pre><code># ls -l</code></pre>
![06](pic2/06.PNG)

#### 建立一個名為 /examdata/change.txt 的空檔案
<pre><code># mkdir examdata
# touch examdata/change.txt</code></pre>
#### 修改檔案相關資料
檔案的擁有者為 sshd
<pre><code># chown sshd change.txt</code></pre>
擁有群組為 users
<pre><code># chgrp users change.txt</code></pre>
sshd 可讀可寫，users 群組成員可讀， 其他人沒權限
<pre><code># chmod 640 change.txt</code></pre>
修改日期調整成 2012 年 12 月 21 日
<pre><code># touch -t 1212210000 change.txt</code></pre>
最後確認修改結果
<pre><code># ls -l</code></pre>
![07](pic2/07.PNG)


