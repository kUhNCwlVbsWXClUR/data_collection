# data_collection

### 数据采集技术

scrapy[twisted]: 时下python最流行的爬虫框架， 可用于数据的采集
scrapy-redis： 用于分布式采集(用于大并发采集)

### 存储
- mongodb
- mysql
- redis

###数据采集出现的问题

### 1. 账号限制

<p>
    准备适量多的账号
    使用selenium登录, 并将登录过程中的cookies信息保存下来,存在文件或者数据库中,推荐采用redis
    给scrapy采集程序添加 CookiesMiddleware
</p>

### 2. IP限制

<p>
    准备适量的IP地址
    给scrapy采集程序添加 ProxiesMiddleware
</p>

### 3. 登录时验证码问题

- 常用的验证码
    1. 滑块验证码
        使用 selenium 进行拖曳即可
    2. 少量简单字符验证码
        进行标注
        使用 opencv 对字符验证码进行切割(简单就是取出前景色, 先进行滤波后二值化，再找到轮廓,根据字母所占图片的比例，进行切割)
        将清洗好的单个字符图片数据和标注放在相应的模型中进行训练
    3. 点字验证码(大量无法使用人工标注)
        使用tensorflow,或者其他的聚类算法

