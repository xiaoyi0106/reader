# lightink-server

### 部署

wget -O docker-compose.yml https://raw.githubusercontent.com/lightink-qingmo/lightink-server/master/docker-compose.yml


cd /home/docker/qingmo/;docker-compose -f docker-compose.yml pull ; docker-compose -f docker-compose.yml up -d


### API接口

#### baseApi : `http://qingmo.zohar.space/`

#### 搜索

目前支持书名搜索和作者搜索

#### Request

- Method: `GET`
- URL:  ```/:code/:name/search?key=${}```
    - 搜索人道天堂:  ```search?key=${人道天堂}```


##### Response
- Body
```
[
    {
        "author": "荆柯守",//作者
        "name": "人道天堂",//书名
        "link": "/book/rendaotiantang/"//详情的连接
    }
]
```
- - -


#### 详情

查看数据详情和目录

#### Request

- Method: `GET`
- URL:  ```/:code/:name/details?link=${}```
    - 查看搜索出来的数据的详情:  ```/:code/:name/details?link=/book/rendaotiantang/```


##### Response
- Body
```
{
    "cover": "https:///www.daocaorenshuwu.com/uploads/litimg/161206/1-1612061F109556.jpg", //封面
    "summary": " 这是一个未来世界，梦想的起源地，科技的进步，使人类消灭了沉重的体力劳动，第一次由人类内部压迫中开始解放出来 黄金时代的来临，过去数百万年的业力却纠缠不息，消灭或者解脱，一切都在人类自己选择 ",//简介
    "catalogs": [
        {
            "chapterName": "主人公人物卡",//章节名
            "chapterlink": "//www.daocaorenshuwu.com/book/rendaotiantang/585691.html"//内容连接
        },
        {
            "chapterName": "本文涉及的神祇",
            "chapterlink": "//www.daocaorenshuwu.com/book/rendaotiantang/585692.html"
        }
    ],
    "update": "2016-12-06 17:34:46",//更新日期
    "category": "科幻",//分类
    "lastChapter": "第271章 圣道立",//最后一张
    "status": "完结"//状态
}
```

- - -

#### 内容

查看章节内容

#### Request

- Method: `GET`
- URL:  ```/:code/:name/content?href=${}```
    - 查看目录中的chapterlink:  ```/:code/:name/content?href=https://www.daocaorenshuwu.com/book/rendaotiantang/585695.html```


##### Response
- Body
```
{
    "nextText": "下一页", //暂时无用
    "text": "黑暗之中，听到风声四起，雷声隐隐由远而近。.... ", //章节内容
    "nextLink": "上一章" //暂时无用
}
}
```

- - -

#### 获取书源仓库列表

返回楚观git仓库中登记的书源仓库

#### Request

- Method: `GET`
- URL:  ```/book_source/repository```


##### Response
- Body
```
[
    {
        "about": "",
        "author": "纯二",
        "code": "2333",
        "url": "https://gitee.com/chuner821/houmo/raw/master/chuner.json"
    },
    {
        "about": "",
        "author": "旧人",
        "code": "9713",
        "url": "https://gitee.com/tyj9713/BookSourceRepository/raw/master/repository.json"
    }
]
```

- - -

#### 获取指定的${code}书源仓库中的书源的描述

获取指定的${code}书源仓库中的书源的描述

#### Request

- Method: `GET`
- URL:  ```/book_source/description/:code```
    - eg:  ```/book_source/description/2333```


##### Response
- Body
```
{
    "name": "By 纯二",
    "summary": "This is just a book source repository.",
    "list": [
        {
            "name": "My716",
            "url": "http://api.zhuishushenqi.com",
            "category": 3,
            "rank": 41,
            "auth": false,
            "version": 102
        },
        {
            "name": "中学生读物",
            "url": "https://fox2008.cn",
            "category": 0,
            "rank": 12,
            "auth": false,
            "version": 100
        },
        ....
    ],
    "url": "https://gitee.com/chuner821/houmo/raw/master/chuner.json"
}
```

- - -

#### 获取指定的${code}/${name}书源

获取指定的${code}/${name}书源

#### Request

- Method: `GET`
- URL:  ```/book_source/:code/:name```
    - eg:  ```/book_source/2333/My716```


##### Response
- Body
```
太长 从略
```