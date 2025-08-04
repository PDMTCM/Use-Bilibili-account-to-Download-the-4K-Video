# 使用Bilibili 帳戶下載4K 影片

---

## Step 1 . 

首先，要登入Bilibili 帳戶。

```
https://www.bilibili.com/
```

![Bili](http://pdm888.oss-cn-beijing.aliyuncs.com/img/Bili.png) 

![image-20250804004758513](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804004758513.png) 

---

## Step 2 . 

之後使用Google 瀏覽器的 Cookies 擴充元件。

擴充元件的 名稱 ***ookdjilphngeeeghgngjabigmpepanpl***

```
https://chromewebstore.google.com/detail/cookie-editor/ookdjilphngeeeghgngjabigmpepanpl?hl=zh-TW&utm_source=ext_sidebar
```

![image-20250802200535843](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250802200535843.png) 

安裝這個擴充元件後，去到已經登陸帳戶的B站。(當然該帳戶必須是普通付費大會員B站帳戶) ，所以該Cookies 是等於用你的大會員帳戶來下載。

注意假設想匯出該網址的Cookies ，必須在該網址頁面執行。

```
https://www.bilibili.com/
```

用四步來匯出Cookies : 

在Chrome 瀏覽器 上使用擴充元件。

![image-20250804003714900](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804003714900.png) 

按匯出鍵。

![image-20250804004155671](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804004155671.png) 

注意輸出格式為 Netscape 。

![image-20250804004205244](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804004205244.png)****

最後會獲得一個txt檔。記得把名稱更改為 cookies.txt

![image-20250804004538007](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804004538007.png) 

---

## Step 3 . 

我們可以使用PowerShell 來執行command 。

安裝 yt-dlp和ffmpeg  --- command

```
winget install yt-dlp ffmpeg
```

如果需要更新可以用 --- command

```
winget upgrade yt-dlp
```

---

## Step 4 . 

執行編輯系統環境變數

![image-20250804000401724](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804000401724.png) 

![image-20250804000556529](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804000556529.png) 

在 兩個 PATH 輸入 --- command

```
C:\Users\使用者名稱\AppData\Local\Microsoft\WinGet\Packages\Gyan.FFmpeg_Microsoft.Winget.Source_8wekyb3d8bbwe\ffmpeg-7.1.1-full_build\bin
```

![image-20250804000749393](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804000749393.png) 

之後重新開機 (必須的)

---

## Step 5 . 

執行 PowerShell。

![image-20250804001236240](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804001236240.png) 

請注意路徑的設定

![image-20250804001524342](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804001524342.png) 

檢查版本

```
yt-dlp --version
```

```
ffmpeg -version
```

---

## Step 6 . 

我們必須把剛才由擴充元件獲得的Cookies ，放在想下載的文件夾中，即是cookies.txt 的所在路徑必須和Powershell 設定的路徑要相同。 

```
C:\Users\使用者名稱\OneDrive\Desktop\PDM_TCM_TEST
```

![image-20250804002938543](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804002938546.png) 

![image-20250804003023855](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804003023855.png) 

----

## Step 7 . 

 如果想了解該影片的最普通到最佳影像格式是什麼可以輸入這句 --- command

![image-20250804001943030](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804001943030.png) 

白色的部分是B站的影片析別碼，每段影片都有自己唯一的析別碼。

紅色的部分是固定的Command。

```
yt-dlp -F --cookies cookies.txt "https://www.bilibili.com/video/BV1HEf2YWEvs/"
```

![image-20250804005507610](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804005507610.png)

---

## Step 8 . 

 如果想下載該影片的最佳影像格式可以輸入這句 --- command (程式會自動下載最佳的影片格式)

只需要修改紫色的部分便可以了。

![image-20250804010808041](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804010808041.png) 

```
yt-dlp -f "bestvideo+bestaudio/best" --cookies cookies.txt "https://www.bilibili.com/video/BV1HEf2YWEvs/"
```

![image-20250804011204824](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804011204824.png)  

我們也可以手動調教影片下載的格式:

![image-20250804011622361](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804011622361.png) 

````
yt-dlp -f 30125+30280 --cookies cookies.txt "https://www.bilibili.com/video/BV1HEf2YWEvs/"
````

---

## Step 9 .

完成。你已經成功下載影片。

如果是 Youtube ，也可以用同一個方法，但假設不使用帳戶，你是可以無視 cookies 的。

即 這句 command 便可。 (下載)

````
yt-dlp -f "bestvideo+bestaudio/best" "https://www.youtube.com/watch?v=R3GfuzLMPkA"
````

查詢的同樣 (查詢影片所有格式)

````
yt-dlp -F "bestvideo+bestaudio/best" "https://www.youtube.com/watch?v=R3GfuzLMPkA"
````

![image-20250804012357419](http://pdm888.oss-cn-beijing.aliyuncs.com/img/image-20250804012357419.png)

---





