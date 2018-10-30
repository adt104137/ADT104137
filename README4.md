# ADT104137-HW4
## 1. 管理群組共用資料的權限設計
### * 建立群組名稱
<pre><code># groupadd mygroup
# groupadd nogroup</code></pre>
可用grep來搜尋檢查群組及GID
<pre><code># grep mygroup /etc/group</code></pre>
### * 建立帳號名稱、密碼，以及加入群組
創立使用者帳號時，同時加入群組
<pre><code># useradd -g mygroup myuser1</code></pre>
設定密碼
<pre><code># passwd myuser1</code></pre>
檢查使用者UID及GID
<pre><code># id myuser1</code></pre>
![01](pic3/01.PNG)<br/>
可檢視所有帳戶之UID及GID
<pre><code># cat /etc/passwd</code></pre>
![02](pic3/02.PNG)
