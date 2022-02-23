## 接口清单

### 一、首页轮播图

1. 获取首页轮播图信息接口

### 二、Cryptovoxels 相关接口
1. 获取Cryptovoxels Parcel 列表接口
2. 获取Cryptovoxels Event 列表接口

### 三、Decentraland 相关接口
1. 获取Decentraland Parcel 列表接口
2. 获取Decentraland Event 列表接口

### 四、Topic 相关接口
1. 获取首页 Topic 列表接口
2. 获取 Topic 详情页信息接口
3. 获取 Topic 列表页信息接口

### 五、Cryptovoxels 地图相关接口
1. 获取 Cryptovoxels 地图的地块详细信息
2. 获取 Cryptovoxels 第三级地图数据

### 六、Metaverse Analytics 相关接口
1. 获取各元宇宙平台概要信息接口
2. 获取 Cryptovoxels 流量统计信息接口
3. 获取 Cryptovoxels 地块成交均价统计信息接口
4. 获取 Cryptovoxels 地块成交总数量统计信息接口
5. 获取 Cryptovoxels 地块销售总额统计信息接口
6. 获取 Cryptovoxels 地块mint情况统计信息接口
7. 获取 Cryptovoxels 地主总数统计信息接口

----
## 全局错误码

|  Code  | Description                                | Oher                               |
| :----: | :----------------------------------------- | :--------------------------------- |
| 100000 | success                                    |                                    |
| 100001 | param error                                |                                    |

----
## 接口详情
**1\.1 获取首页轮播图信息接口**
###### 接口功能
> 获取首页轮播图信息（包括图片、文字、跳转链接等）

###### URL
> https://api.metacat.world/api/v1/get_carousel_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
> 无

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.total     | int   | 返回数据总条数                                             |
| data.list.img_url     | string   | 轮播图url                                             |
| data.list.title     | string   | 轮播图标题                                             |
| data.list.detail_url     | string   | 轮播图跳转链接                                             |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_carousel_list' | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "total": 3,
    "list": [
      {
        "img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0x195acaf2ccb5d388f4f5a03030ad765d74d94f3f/womps/1639464964429-5727956d-03dd-4363-936f-5a4763206df9.jpg",
        "title": "New eyes for the Sphinx...",
        "detail_url": "https://www.cryptovoxels.com/play?coords=N@9W,296N,6F"
      },
      {
        "img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0xa214384fd96d0883a4e4c75036c2863f0f5995f5/womps/1639464976791-9cf16de0-3ac3-4088-a5c9-2292fad8d0e0.jpg",
        "title": "happy holidays!",
        "detail_url": "https://www.cryptovoxels.com/play?coords=@719E,660S"
      },
      {
        "img_url": "https://www.k1ic.com/imgs/cv_month_sold_sum.png",
        "title": "CV parcel monthly trade sum(ETH)",
        "detail_url": "https://www.k1ic.com/cvb-zh.html"
      }
    ]
  }
}
```
---
**2\.1 获取Cryptovoxels Parcel 列表接口**
###### 接口功能
> 获取Cryptovoxels Parcel页面数据，支持翻页

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| page  | false | int  | 1      | 页码           |
| count | false | int  | 50     | 每页返回的条数 |
| query | false | string  |     | 查询词，长度不超过256 |
| type | false | string  |   all  | 筛选类型，接口中返回 |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.page     | int   | 当前页码                                            |
| data.count     | int   | 当前页返回的parcel_list总条数                                          |
| data.total\_page     | int   | 总页数，供翻页使用                                         |
| data.query     | int   | 当前页面的搜索词                                        |
| data.type     | int   | 当前页面的筛选类型                                       |
| data.type\_total     |   | 当前搜索词或筛选类型命中的类型明细，及每种类型的总数                                      |
| data.parcel\_list.name    |  string  |  场馆名称                                      |
| data.parcel\_list.description   |  string  |  场馆简介                                      |
| data.parcel\_list.type   |  string  |  场馆类型，显示在场馆封面图左上角                                      |
| data.parcel\_list.cover\_img\_url   |  string  |  场馆封面图url                                      |
| data.parcel\_list.opensea\_url   |  string  |  场馆对应opensea url                                     |
| data.parcel\_list.parcel\_page\_url   |  string  |  场馆详情页 url                                     |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_cv_parcel_list' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "page": 1,
    "count": 3,
    "total_page": 2185,
    "query": "",
    "type": "all",
    "type_total": {
      "all": 6554,
      "gallery": 419,
      "MVB": 130,
      "tower": 74,
      "HQ": 71,
      "house": 60,
      "club": 53,
      "museum": 40,
      "garden": 35,
      "temple": 32,
      "shop": 28,
      "other": 5612
    },
    "parcel_list": [
      {
        "parcel_id": 4,
        "name": "@westcoastbill 21x: glass age",
        "description": "www.twitter.com/westcoastbill",
        "type": "other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0xab43a7ff49943acb0d77bbb8bc1a2c911c473d48/womps/1637842579139-27503614-dcb9-4882-9ae0-cae7d9af861d.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/4",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/4"
      },
      {
        "parcel_id": 1,
        "name": "@westcoastbill 21x: space age",
        "description": "Thank you Nick/Ben.  We won't let you down. leandro and @westcoastbill - http://twitter.com/westcoastbill www.21x.com",
        "type": "other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0x2401934ab882a6e66bbea33cd8d7e10e6990c283/womps/1638266003900-6bf35b63-742a-4d9f-ba71-fea8b9be9ebc.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/1",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/1"
      },
      {
        "parcel_id": 2,
        "name": "Welcome!",
        "description": "Welcome to Cryptovoxels! This build was done by the skilled and talented Devil to show our new custom tiles features. Explore to find some tips and tricks of how to explore the world.",
        "type": "other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0x1168652fd8553de2ca689793c0f7f975ae15d4f8/womps/1639359337606-4eebfbee-550a-4e23-a92a-1c78ec67c48b.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/2",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/2"
      }
    ]
  }
}
```
---
**2\.2 获取Cryptovoxels Event 列表接口**
###### 接口功能
> 获取Cryptovoxels Event页面数据，支持下拉加载更多

###### URL
> https://api.metacat.world/api/v1/get_cv_event_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| cursor  | false | int  | 1      | 获取第二页及之后每页数据时传入的游标           |
| count | false | int  | 10     | 每次请求返回的条数 |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.cursor     | int   | 请求下一页数据时传入的游标                                           |
| data.count     | int   | 本次接口返回的event_list数据条数，若该值为0，则无需再次下拉刷新                                          |
| data. event_list.name     | string   |  活动名字                                             |
| data. event_list.description     | string   |  活动简介                                             |
| data. event_list.cover_img     | string   |  活动封面图地址                                           |
| data. event_list.event_detail_url     | string   |  活动详情页url                                           |
| data. event_list.event_parcel_url     | string   |  活动场馆url                                           |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_cv_event_list' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "cursor": 102,
    "count": 3,
    "event_list": [
      {
        "name": "Movie Night @ Suzie's",
        "description": "Watch a short 35 minutes movie answering the question where does evil comes from. Directed by Kristina Weiserova  Prague.",
        "cover_img": "https://media-crvox.sfo2.digitaloceanspaces.com/0x5696a8ba76ff5c6f6e1e46c20925f5a056167a2b/womps/1639320550849-955fb1ff-7206-4451-86c0-c0113036cf31.jpg",
        "activity_time": "2021/12/10/10:00 -- 2021/12/10/12:00",
        "event_detail_url": "https://www.cryptovoxels.com/events/1018",
        "event_parcel_url": "https://www.cryptovoxels.com/parcels/5626"
      },
      {
        "name": "Cryptovoxels Champion",
        "description": "Daily trading data and visitor data for Cryptovoxels. Welcome come to have a view! for more info please view https://www.k1ic.com/cvb-zh.html",
        "cover_img": "https://media-crvox.sfo2.digitaloceanspaces.com/0x1aa049f3a3278d47de393dca77e5f918bc1e157c/womps/1635632769008-73ffb78c-fc80-4431-88ce-39ad3f865c5a.jpg",
        "activity_time": "2021/12/09/01:05 -- 2021/12/10/00:05",
        "event_detail_url": "https://www.cryptovoxels.com/events/1068",
        "event_parcel_url": "https://www.cryptovoxels.com/parcels/4495"
      },
      {
        "name": "Midnight Breeze pre-reveal party extravaganza",
        "description": "The event will include a possible POAP & WHITELIST  a final trailer with the RELEASE DATE AHHHHH Face  music by @Harrisonfirst and lots of good vibes. I can not wait to share this moment with you all  it has really been a journey and I am so excited. BYO drinks ;)  PS: lots of artists  collectors and investors are joining the part. A great opportunity to make some new connections!",
        "cover_img": "https://media-crvox.sfo2.digitaloceanspaces.com/0x76ef45f256587238ae279e957cc5e84bb3b3aaf1/womps/1638921908491-0a1220d0-c7f1-4637-8213-ef9b85e89b46.jpg",
        "activity_time": "2021/12/08/06:00 -- 2021/12/08/08:00",
        "event_detail_url": "https://www.cryptovoxels.com/events/1062",
        "event_parcel_url": "https://www.cryptovoxels.com/parcels/4710"
      }
    ]
  }
}
```
---
**3\.1 获取Decentraland Parcel 列表接口**
###### 接口功能
> 获取Decentraland Parcel页面数据，支持翻页

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| page  | false | int  | 1      | 页码           |
| count | false | int  | 50     | 每页返回的条数 |
| query | false | string  |     | 查询词，长度不超过256 |
| type | false | string  |   all  | 筛选类型，接口中返回 |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.page     | int   | 当前页码                                            |
| data.count     | int   | 当前页返回的parcel_list总条数                                          |
| data.total\_page     | int   | 总页数，供翻页使用                                         |
| data.query     | int   | 当前页面的搜索词                                        |
| data.type     | int   | 当前页面的筛选类型                                       |
| data.type\_total     |   | 当前搜索词或筛选类型命中的类型明细，及每种类型的总数                                      |
| data.parcel\_list.name    |  string  |  场馆名称                                      |
| data.parcel\_list.description   |  string  |  场馆简介                                      |
| data.parcel\_list.type   |  string  |  场馆类型，显示在场馆封面图左上角                                      |
| data.parcel\_list.cover\_img\_url   |  string  |  场馆封面图url                                      |
| data.parcel\_list.opensea\_url   |  string  |  场馆对应opensea url                                     |
| data.parcel\_list.parcel\_page\_url   |  string  |  场馆详情页 url                                     |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_dcl_parcel_list' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "page": 1,
    "count": 3,
    "total_page": 15578,
    "query": "",
    "type": "all",
    "type_total": {
      "all": 46732,
      "gallery": 257,
      "house": 83,
      "shop": 53,
      "tower": 45,
      "HQ": 36,
      "garden": 33,
      "museum": 32,
      "club": 25,
      "temple": 11,
      "other": 46157
    },
    "parcel_list": [
      {
        "parcel_id": "2092",
        "internal_type": "estate",
        "name": "AETHERIAN project",
        "description": "Aetherian City will be one of the main attractions for visitors and dwellers of Decentraland, as it intends to be the largest cyberpunk-agglomeration of the metaverse.",
        "type": "other",
        "cover_img_url": "https://api.decentraland.org/v1/estates/2092/map.png",
        "opensea_url": "https://opensea.io/assets/0x959e104e1a4db6317fa58f8295f586e1a978c297/2092",
        "parcel_page_url": "https://market.decentraland.org/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/2092"
      },
      {
        "parcel_id": "1976",
        "internal_type": "estate",
        "name": "Dragon City",
        "description": "A perfect combination of China’s ancient culture and Western modernization, a reflection of both the Eastern and Western civilizations.",
        "type": "other",
        "cover_img_url": "https://api.decentraland.org/v1/estates/1976/map.png",
        "opensea_url": "https://opensea.io/assets/0x959e104e1a4db6317fa58f8295f586e1a978c297/1976",
        "parcel_page_url": "https://market.decentraland.org/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/1976"
      },
      {
        "parcel_id": "1769",
        "internal_type": "estate",
        "name": "District X",
        "description": "Decentraland’s premier land, content, and service company providing land rentals/leases, prefab and custom content, and in-world services.",
        "type": "other",
        "cover_img_url": "https://api.decentraland.org/v1/estates/1769/map.png",
        "opensea_url": "https://opensea.io/assets/0x959e104e1a4db6317fa58f8295f586e1a978c297/1769",
        "parcel_page_url": "https://market.decentraland.org/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/1769"
      }
    ]
  }
}
```
---
**3\.2 获取Decentraland Event 列表接口**
###### 接口功能
> 获取Decentraland Event页面数据，支持下拉加载更多

###### URL
> https://api.metacat.world/api/v1/get_dcl_event_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| cursor  | false | int  | 1      | 获取第二页及之后每页数据时传入的游标           |
| count | false | int  | 10     | 每次请求返回的条数 |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.cursor     | int   | 请求下一页数据时传入的游标                                           |
| data.count     | int   | 本次接口返回的event_list数据条数，若该值为0，则无需再次下拉刷新                                          |
| data. event_list.name     | string   |  活动名字                                             |
| data. event_list.description     | string   |  活动简介                                             |
| data. event_list.cover\_img     | string   |  活动封面图地址                                           |
| data. event_list.event\_detail\_url     | string   |  活动详情页url                                           |
| data. event_list.event\_parcel\_url     | string   |  活动场馆url                                           |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_dcl_event_list' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "cursor": 102,
    "count": 3,
    "event_list": [
      {
        "name": "NFTcreep Mesuem",
        "description": "Featuring artists from all over the world. ",
        "cover_img": "https://events.decentraland.org/poster/29ad7b706182f979.jpg",
        "activity_time": "2021/11/03/21:01 -- 2021/12/31/22:01",
        "event_detail_url": "https://events.decentraland.org/event/?id=2509615f-1b7c-4fca-ba80-fa5bd2767013",
        "event_parcel_url": "https://play.decentraland.org/?position=-73,-32"
      },
      {
        "name": "Opportunity! First free mintable golf club, only 100 supply!",
        "description": "We are glad to announce that GolfCraft players are now able to mint his first golf club NFT for free.\n\nFor more info:\n\nDiscord: http://discord.gg/FyffSWF235\n\nTwitter: https://twitter.com/GolfcraftGame",
        "cover_img": "https://events.decentraland.org/poster/26df7a2c6190c57a.png",
        "activity_time": "2021/11/14/20:00 -- 2022/11/30/20:00",
        "event_detail_url": "https://events.decentraland.org/event/?id=29e70280-1ca4-4866-abe1-de5b0f1e6899",
        "event_parcel_url": "https://market.decentraland.org/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/3709"
      },
      {
        "name": "Archverse北碚——现代化建设与集团生活 | Archverse Beibei: Modernization and Group Life",
        "description": "在Decentraland中，我们做了两件事，一是对北碚西部科学院、北温泉公园、知名文学家住所等建筑等复原，二是用历史图片、刊物等内容筹建北碚的现代化建设与集团生活的展览，让建筑和展览共同作为Decentraland中北碚的基底。后续，我们将开放共同书写的信息平台，让大家在其中讲述自己的故事。\n\nOn Decentraland, we have mainly put two things into practice. Firstly, we restored several the Science Institute of West China, the Northern Hot Spring Park and famous litterateurs’ residences; Secondly, historical pictures and publications were used for curating the exhibition “Archverse Beibei: Modernization and Group Life”, and laying down the foundation with both architecture and exhibition for Decentraland Beibei. For future updates, we intend to open an information platform for co-writing and let everyone share their stories.\n",
        "cover_img": "https://events.decentraland.org/poster/78cb7d2b619ba181.jpg",
        "activity_time": "2021/11/27/00:00 -- 2022/01/27/00:00",
        "event_detail_url": "https://events.decentraland.org/event/?id=cefcd032-130b-4a0c-a7e8-e4d7cda1b222",
        "event_parcel_url": "https://market.decentraland.org/contracts/0x959e104e1a4db6317fa58f8295f586e1a978c297/tokens/1976"
      }
    ]
  }
}
```
---
**4\.1 获取首页 Topic 列表接口**
###### 接口功能
> 获取首页 Topic 列表接口，只返回4条数据

###### URL
> https://api.metacat.world/api/v1/get_topic_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -     | -           |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.total     | int   | 本次返回的list总条数                                             |
| data.list.topic_id     | int   | 请求topic详情页时，传入该参数    |
| data.list.name     | string   | topic名称    |
| data.list.type     | string   | topic类型，显示在Topic封面右上角    |
| data.list.img_url_list     | list   | topic封面图，4张小图对应的url    |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_topic_list' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "total": 7,
    "list": [
      {
        "topic_id": 100,
        "name": "PonlaiiDesign",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x01e0c7b70e0e05a06c7cc8deeb97fa03d6a77c9c/womps/1634867345988-16f1df8c-fc8d-492f-86f8-0184e0977697.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x38bbd375d49d6237984cbfa19719c419af9fe514/womps/1635510125681-66458a25-8e86-4082-939b-409d0669e136.jpg",
          "https://www.cryptovoxels.com/api/womps/19637.jpg",
          "https://www.cryptovoxels.com/api/womps/18000.jpg"
        ]
      },
      {
        "topic_id": 101,
        "name": "MetaEstate",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xba855ad3608d3428df17a5cd4a67a8a37fb71702/womps/1640198213165-c394e11b-d7c0-4cd2-8020-addb1b188662.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xc0beefeed699f6d6a08397fcbf8fbadf9f83eb5d/womps/1640245498965-8fe18578-e1e9-42e5-96b8-b6bd51883b33.jpg",
          "https://www.cryptovoxels.com/api/womps/20271.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xd67c34169b372d5b3932c548a940d4ea74fe7af5/womps/1640475109165-3896a982-1ab5-4c3d-80b2-47ed43345018.jpg"
        ]
      },
      {
        "topic_id": 102,
        "name": "BCA",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x43259da836f9c0576ee23821d58e8fd025ba187a/womps/1640273956783-785f2b45-ca14-4e1c-bbf0-45ed0ac0a125.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xd67c34169b372d5b3932c548a940d4ea74fe7af5/womps/1640587579436-35715c20-e77d-4ec1-9695-15fbd52ca476.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa8093c09098452727492968ddfe4a0e033ab76bd/womps/1637657931992-7a2ef5e0-190f-412f-b09f-59c439b3d8e9.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa8093c09098452727492968ddfe4a0e033ab76bd/womps/1637658522776-db362d6d-ef18-4b39-95ff-5415da26d09a.jpg"
        ]
      },
      {
        "topic_id": 103,
        "name": "MetaLandscape",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa32c90129e5a78ff2f5984d306f12cc813dd2cda/womps/1638770908853-20aaf49b-a446-4780-901c-5e05a69b7f22.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa32c90129e5a78ff2f5984d306f12cc813dd2cda/womps/1640262479487-fbf0a779-c538-40f9-b820-c07d9273a5b7.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xd67c34169b372d5b3932c548a940d4ea74fe7af5/womps/1640588885443-cd1b0d26-c80e-491e-8e42-94f6facac1f3.jpg",
          "https://poster-phi.vercel.app/metacat_logo.png"
        ]
      },
      {
        "topic_id": 104,
        "name": "Voxel Architects",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x1e11654ceff26e4bc3e71928432d6b864896c62a/womps/1640217962676-bda56374-56d2-4f8b-8568-3d0e9bee5a8e.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x41c851d34ea8e954ae05f06bb652dae71c5662d1/womps/1640308635422-85cb82eb-10da-426a-87ec-f27f52a9067e.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x41c851d34ea8e954ae05f06bb652dae71c5662d1/womps/1640037341533-68181ebf-a751-4ec5-8d32-77da3037a3f6.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x87DdB931310238874437458Ab7D1BBA4d1C89525/womps/1640383137402-54c1da86-fc4c-4b7f-b84a-7f3eff47d000.jpg"
        ]
      },
      {
        "topic_id": 105,
        "name": "Evilvoxels",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xb823dc506011eedab6f8feecc88806dbfc55ea93/womps/1640280419316-f5a052c3-1c05-4635-9c00-acf77eaed1d6.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x1e11654ceff26e4bc3e71928432d6b864896c62a/womps/1640219549116-114a48e3-ff78-413b-ba8f-4fb8074aecd5.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xb823dc506011eedab6f8feecc88806dbfc55ea93/womps/1640276480467-532d8be5-cadc-4519-9b13-d85bd4206827.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x473b2702c302ef6df351004cbc4d16b5cecc804c/womps/1640282394980-41fdd179-8b94-4590-ab3c-560d5aca44f1.jpg"
        ]
      },
      {
        "topic_id": 106,
        "name": "TopBidder",
        "type": "Topic",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x8ed10ca1c0b15353894eecea9e6bc11f15d53e10/womps/1638854299202-25099b58-5ae1-4145-8d7e-eb5f340998c3.jpg",
          "https://www.cryptovoxels.com/api/womps/4011.jpg",
          "https://www.cryptovoxels.com/api/womps/20019.jpg",
          "https://www.cryptovoxels.com/api/womps/5571.jpg"
        ]
      }
    ]
  }
}

```
---
**4\.2 获取 Topic 详情页信息接口**
###### 接口功能
> 获取 Topic 详情页信息接口，一次返回Topic下的所有场馆数据

###### URL
> https://api.metacat.world/api/v1/get_topic_detail

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| id  | ture | int  | 100    | topic_id          |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.base_info.logo_url     | string   | 详情页顶部，机构logo url        |
| data.base_info.name     | string   | 详情页顶部，机构名称（显示在机构logo下方）        |
| data.base_info.description     | string   | 详情页顶部，机构简介（显示在机构联系方式下方）        |
| data.base_info.website     | string   | 详情页顶部，机构官网        |
| data.base_info.twitter     | string   | 详情页顶部，机构官方twitter        |
| data.base_info.discord     | string   | 详情页顶部，机构官方discord        |
| data.parcel\_list.name    |  string  |  场馆名称                                      |
| data.parcel\_list.description   |  string  |  场馆简介                                      |
| data.parcel\_list.type   |  string  |  场馆类型（页面展示忽略该值）                                      |
| data.parcel\_list.cover\_img\_url   |  string  |  场馆封面图url                                      |
| data.parcel\_list.opensea\_url   |  string  |  场馆对应opensea url                                     |
| data.parcel\_list.parcel\_page\_url   |  string  |  场馆详情页 url                                     |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_topic_detail?id=103' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "base_info": {
      "logo_url": "https://poster-phi.vercel.app/topic/logo/MetaLandscape_logo.png",
      "name": "MetaLandscape",
      "description": "ALL FOR METAVERSE",
      "website": "",
      "twitter": "https://twitter.com/ConFi0419",
      "discord": ""
    },
    "parcel_list": [
      {
        "parcel_id": 4540,
        "name": "ConFi's Crystal Ball",
        "description": "None",
        "type": "Other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0xa32c90129e5a78ff2f5984d306f12cc813dd2cda/womps/1640262479487-fbf0a779-c538-40f9-b820-c07d9273a5b7.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/4540",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/4540"
      },
      {
        "parcel_id": 3415,
        "name": "Red Romance",
        "description": "The Black Fractal Gallery on Proton Island",
        "type": "Other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0xa32c90129e5a78ff2f5984d306f12cc813dd2cda/womps/1638770908853-20aaf49b-a446-4780-901c-5e05a69b7f22.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/3415",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/3415"
      },
      {
        "parcel_id": 5249,
        "name": "Parcel_Id: 5249",
        "description": "None",
        "type": "Other",
        "cover_img_url": "https://www.cryptovoxels.com/api/womps/19153.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/5249",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/5249"
      }
    ]
  }
}

```
---
**4\.3 获取 Topic 列表页信息接口**
###### 接口功能
> 获取 Topic 列表页信息接口，带分页逻辑

###### URL
> https://api.metacat.world/api/v1/get_builder_list

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| page  | false | int  | 1    |          |
| count  | false | int  | 50    |          |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.page     | int   | 当前页码                                             |
| data.count     | int   | 当前页返回的总条数                                             |
| data.total_page     | int   | 总页数                                             |


###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_builder_list?page=4&count=3' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "page": 1,
    "count": 3,
    "total_page": 8,
    "list": [
      {
        "topic_id": 100,
        "name": "PonlaiiDesign",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x38bbd375d49d6237984cbfa19719c419af9fe514/womps/1640789121816-fd81a23c-be06-44cc-93df-67232c023196.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x33718d7bf5bdab246409443dda7494aab795095b/womps/1640791793522-41212cc7-d83c-49f9-81d5-4dc58d1196ae.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x38bbd375d49d6237984cbfa19719c419af9fe514/womps/1640789937819-62e96e3d-4a1b-4353-be33-06cebaad4642.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x38bbd375d49d6237984cbfa19719c419af9fe514/womps/1640789490467-1e4b0aac-08cd-486d-a840-00336cbab069.jpg"
        ]
      },
      {
        "topic_id": 101,
        "name": "MetaEstate",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x10c919762aee011b0f62964c6e9051dc482764fb/womps/1642658941111-8424f63a-f63b-40cc-9b00-b0586e0d52a0.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xc0beefeed699f6d6a08397fcbf8fbadf9f83eb5d/womps/1640245498965-8fe18578-e1e9-42e5-96b8-b6bd51883b33.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x41c851d34Ea8e954ae05F06Bb652DaE71c5662D1/womps/1643654817336-e95c8f06-1e55-4057-bfcc-3d3b853ed694.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0x411e07616e24fed46c647ef3a6325d4c7d0645eb/womps/1641820017142-1e516370-0ff7-4f74-beaf-dec81c2153b3.jpg"
        ]
      },
      {
        "topic_id": 102,
        "name": "BCA",
        "img_url_list": [
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xffc0695bc801b68c7ce5503b11c8bc0afab47b33/womps/1642139873697-c66a81d3-1c15-463f-9618-108daa32ade0.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xd67c34169b372d5b3932c548a940d4ea74fe7af5/womps/1643703170129-94c80ae7-f840-4812-80bf-0864350f2612.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa8093c09098452727492968ddfe4a0e033ab76bd/womps/1637657931992-7a2ef5e0-190f-412f-b09f-59c439b3d8e9.jpg",
          "https://media-crvox.sfo2.digitaloceanspaces.com/0xa8093c09098452727492968ddfe4a0e033ab76bd/womps/1637658522776-db362d6d-ef18-4b39-95ff-5415da26d09a.jpg"
        ]
      }
    ]
  }
}
```
---
**5\.1 获取 Cryptovoxels 地图的地块详细信息**
###### 接口功能
> 获取 Cryptovoxels 地块详细信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_detail

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| id  | true | int  | 1    | 地块id    |
| map_type  | false | string  | traffic  | 地图类型， traffic：流量热力图；price：价格热力图   |
| time_range  | false | string  | quarter   | 地图类型为 price 时，传入该值，month：最近30天；quarter：最近90天；year：最近365天；all：所有时间范围  |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |
| data.parcel_id     | int   | parcel_id（地块id）      |
| data.name     | string   | 地块名称      |
| data.cover_img_url     | string   | 地块封面图       |
| data.opensea_url     | string   |    地块对应的opensea链接     |
| data.parcel_page_url     | string   |  地块对应的 cryptovoxels 页面链接      |
| data.island     | string   |   地块所属的岛名      |
| data.suburb     | string   |     地块所属的街区名    |
| data.traffic.week     | int   |   地块最近7天流量     |
| data.traffic.month    | int   |  地块最近30天流量       |
| data.traffic.all     | int   |    地块总流量     |
| data.last_price.eth    | float   |    地块最后一次交易金额对应的eth     |
| data.last_price.usd     | int   |   地块最后一次交易金额对应的usd      |

###### 接口示例 1
> curl -s 'https://api.metacat.world/api/v1/get_cv_parcel_detail?id=12' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "parcel_id": 12,
    "name": "The Metalith Throne",
    "cover_img_url": "https://www.cryptovoxels.com/api/womps/16509.jpg",
    "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/12",
    "parcel_page_url": "https://www.cryptovoxels.com/parcels/12",
    "island": "Origin City",
    "suburb": "The Center",
    "traffic": {
      "week": 1769,
      "month": 4920,
      "all": 87883
    },
    "last_price": {
      "eth": 1.57,
      "usd": 3569
    }
  }
}
```

###### 接口示例 2
> curl -s 'https://api.metacat.world/api/v1/get_cv_parcel_detail?id=241&map_type=price&time_range=all' | jq . 

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "parcel_id": 241,
    "name": "abcd",
    "cover_img_url": "https://www.cryptovoxels.com/api/womps/15723.jpg",
    "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/241",
    "parcel_page_url": "https://www.cryptovoxels.com/parcels/241",
    "island": "Origin City",
    "suburb": "North Terrace",
    "time_range_sale": {
      "eth": "31.14",
      "usd": 53212
    },
    "last_sale_list": [
      {
        "date": "2022.01.06",
        "eth": "8.00",
        "usd": 28455,
        "is_primary": 0
      },
      {
        "date": "2021.03.11",
        "eth": "5.75",
        "usd": 10363,
        "is_primary": 0
      }
    ]
  }
}
```
---
**5\.2 获取 Cryptovoxels 第三级地图数据**
###### 接口功能
> 获取 Cryptovoxels 第三级地图数据接口

###### URL
> https://api.metacat.world/api/v1/get_cv_map_level_three

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
	"code": 100000,
	"msg": "success",
	"data": {
		"stats": {
			"traffic": {
				"week": {
					"min": 1,
					"max": 12721
				},
				"month": {
					"min": 1,
					"max": 21287
				},
				"all": {
					"min": 0,
					"max": 137360
				}
			}
		},
		"parcels": [{
				"properties": {
					"parcel_id": 4050,
					"name": null,
					"island": "Berlin",
					"suburb": "Berlin"
				},
				"geometry": {
					"type": "Polygon",
					"crs": {
						"type": "name",
						"properties": {
							"name": "EPSG:3857"
						}
					},
					"coordinates": [
						[
							[-7.129899995, -7.11],
							[-6.98, -7.11],
							[-6.98, -7.26],
							[-7.129899995, -7.26],
							[-7.129899995, -7.11]
						]
					]
				},
				"streets": [{
						"properties": {
							"id": 1630,
							"name": "Axel-Springer-Str",
							"island": "Berlin",
							"kind": null,
							"visible": true
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[-6.96, -7.52],
								[-6.96, -6.4]
							]
						}
					},
					{
						"properties": {
							"id": 1654,
							"name": "Lilienthalstraße",
							"island": "Berlin",
							"kind": null,
							"visible": true
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[-6.96, -7.27],
								[-6.4, -7.27]
							]
						}
					},
					{
						"properties": {
							"id": 1682,
							"name": "Brandesstraße",
							"island": "Berlin",
							"kind": null,
							"visible": true
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[-7.26, -7.09],
								[-6.96, -7.09]
							]
						}
					},
					{
						"properties": {
							"id": 1683,
							"name": "Ritterstraße",
							"island": "Berlin",
							"kind": null,
							"visible": true
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[-7.26, -7.28],
								[-6.96, -7.28]
							]
						}
					},
					{
						"properties": {
							"id": 1700,
							"name": "Gröbenufer",
							"island": "Berlin",
							"kind": null,
							"visible": true
						},
						"geometry": {
							"type": "LineString",
							"coordinates": [
								[-6.96, -7.08],
								[-6.69, -7.08]
							]
						}
					}
				],
				"traffic": {
					"week": 24,
					"month": 82,
					"all": 3833
				}
			}
		}
	}
```
---
**6\.1 获取各元宇宙平台概要信息接口**
###### 接口功能
> 获取各元宇宙平台概要信息接口

###### URL
> https://api.metacat.world/api/v1/get_worlds_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": [
    {
      "name": "Cryptovoxels",
      "total_parcel_sales": {
        "value": 20069,
        "symbol": "ETH"
      },
      "number_of_parcel_sales": 6499,
      "total_parcel_supply": 7336,
      "total_land_owner": 2160,
      "total_traffic": 20468022
    },
    {
      "name": "Decentraland",
      "total_parcel_sales": {
        "value": 104302427,
        "symbol": "USD"
      },
      "number_of_parcel_sales": 11321,
      "total_parcel_supply": 92598,
      "total_land_owner": 5308,
      "total_traffic": 0
    }
  ]
}
```
---
**6\.2 获取 Cryptovoxels 流量统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 流量统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_traffic_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "monthly": {
      "data": [
        {
          "time": "2019.09",
          "value": 216856,
          "type": "all"
        },
        {
          "time": "2019.10",
          "value": 243541,
          "type": "all"
        },
        {
          "time": "2019.11",
          "value": 302170,
          "type": "all"
        },
        {
          "time": "2019.12",
          "value": 330170,
          "type": "all"
        },
        {
          "time": "2020.01",
          "value": 392747,
          "type": "all"
        },
        {
          "time": "2020.02",
          "value": 496149,
          "type": "all"
        },
        {
          "time": "2020.03",
          "value": 563487,
          "type": "all"
        },
        {
          "time": "2020.04",
          "value": 151320,
          "type": "all"
        },
        {
          "time": "2020.05",
          "value": 400318,
          "type": "all"
        },
        {
          "time": "2020.06",
          "value": 377516,
          "type": "all"
        },
        {
          "time": "2020.07",
          "value": 318256,
          "type": "all"
        },
        {
          "time": "2020.08",
          "value": 268795,
          "type": "all"
        },
        {
          "time": "2020.09",
          "value": 286729,
          "type": "all"
        },
        {
          "time": "2020.10",
          "value": 398606,
          "type": "all"
        },
        {
          "time": "2020.11",
          "value": 484243,
          "type": "all"
        },
        {
          "time": "2020.12",
          "value": 497008,
          "type": "all"
        },
        {
          "time": "2021.01",
          "value": 478027,
          "type": "all"
        },
        {
          "time": "2021.02",
          "value": 735253,
          "type": "all"
        },
        {
          "time": "2021.03",
          "value": 1385395,
          "type": "all"
        },
        {
          "time": "2021.04",
          "value": 1591459,
          "type": "all"
        },
        {
          "time": "2021.05",
          "value": 1564293,
          "type": "all"
        },
        {
          "time": "2021.06",
          "value": 1448315,
          "type": "all"
        },
        {
          "time": "2021.07",
          "value": 1429352,
          "type": "all"
        },
        {
          "time": "2021.08",
          "value": 1138015,
          "type": "all"
        },
        {
          "time": "2021.09",
          "value": 834697,
          "type": "all"
        },
        {
          "time": "2021.10",
          "value": 1055954,
          "type": "all"
        },
        {
          "time": "2021.11",
          "value": 1082945,
          "type": "all"
        },
        {
          "time": "2021.12",
          "value": 1223326,
          "type": "all"
        },
        {
          "time": "2022.01",
          "value": 1076354,
          "type": "all"
        },
        {
          "time": "2022.02",
          "value": 509081,
          "type": "all"
        }
      ]
    }
  }
}
```
---
**6\.3 获取 Cryptovoxels 地块成交均价统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 地块成交均价统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_avg_price_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "daily": {
      "data": {
        "eth": [
          {
            "time": "2022.01.25",
            "value_avg": 2.29,
            "value_min": 1.56,
            "value_max": 3.73,
            "type": "primary"
          },
          {
            "time": "2022.01.25",
            "value_avg": 3.07,
            "value_min": 2.2,
            "value_max": 4.2,
            "type": "secondary"
          },
          {
            "time": "2022.01.26",
            "value_avg": 1.83,
            "value_min": 1.36,
            "value_max": 3.14,
            "type": "primary"
          },
          {
            "time": "2022.01.26",
            "value_avg": 2.19,
            "value_min": 1.3,
            "value_max": 3.9,
            "type": "secondary"
          },
          {
            "time": "2022.01.27",
            "value_avg": 2.22,
            "value_min": 1.54,
            "value_max": 3.87,
            "type": "primary"
          },
          {
            "time": "2022.01.27",
            "value_avg": 3.31,
            "value_min": 1.59,
            "value_max": 6,
            "type": "secondary"
          },
          {
            "time": "2022.01.28",
            "value_avg": 1.88,
            "value_min": 1.47,
            "value_max": 2.5,
            "type": "primary"
          },
          {
            "time": "2022.01.28",
            "value_avg": 1.58,
            "value_min": 1.22,
            "value_max": 2.17,
            "type": "secondary"
          },
          {
            "time": "2022.01.29",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.29",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.01.30",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.30",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.01.31",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.31",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.01",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.01",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.03",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.03",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.04",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.04",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.05",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.05",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.06",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.06",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.07",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.07",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.08",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.08",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.09",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.09",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.10",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.10",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.11",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.11",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.12",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.12",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.13",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.13",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.14",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.14",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.15",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.15",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.16",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.16",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.17",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.17",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.19",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.19",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.20",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.20",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.21",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.21",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.22",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.22",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.23",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.23",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          }
        ],
        "usd": [
          {
            "time": "2022.01.25",
            "value_avg": 5597,
            "value_min": 3816,
            "value_max": 9123,
            "type": "primary"
          },
          {
            "time": "2022.01.25",
            "value_avg": 7518,
            "value_min": 5385,
            "value_max": 10280,
            "type": "secondary"
          },
          {
            "time": "2022.01.26",
            "value_avg": 4560,
            "value_min": 3378,
            "value_max": 7830,
            "type": "primary"
          },
          {
            "time": "2022.01.26",
            "value_avg": 5456,
            "value_min": 3240,
            "value_max": 9722,
            "type": "secondary"
          },
          {
            "time": "2022.01.27",
            "value_avg": 5841,
            "value_min": 4056,
            "value_max": 10165,
            "type": "primary"
          },
          {
            "time": "2022.01.27",
            "value_avg": 8708,
            "value_min": 4179,
            "value_max": 15773,
            "type": "secondary"
          },
          {
            "time": "2022.01.28",
            "value_avg": 4654,
            "value_min": 3635,
            "value_max": 6199,
            "type": "primary"
          },
          {
            "time": "2022.01.28",
            "value_avg": 3924,
            "value_min": 3030,
            "value_max": 5374,
            "type": "secondary"
          },
          {
            "time": "2022.01.29",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.29",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.01.30",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.30",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.01.31",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.01.31",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.01",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.01",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.03",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.03",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.04",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.04",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.05",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.05",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.06",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.06",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.07",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.07",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.08",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.08",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.09",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.09",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.10",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.10",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.11",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.11",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.12",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.12",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.13",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.13",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.14",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.14",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.15",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.15",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.16",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.16",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.17",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.17",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.19",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.19",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.20",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.20",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.21",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.21",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.22",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.22",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          },
          {
            "time": "2022.02.23",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02.23",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          }
        ]
      }
    },
    "monthly": {
      "data": {
        "eth": [
          {
            "time": "2019.09",
            "value_avg": 0.49,
            "value_min": 0.23,
            "value_max": 1.18,
            "type": "primary"
          },
          {
            "time": "2019.09",
            "value_avg": 0.97,
            "value_min": 0.4,
            "value_max": 5.5,
            "type": "secondary"
          },
          {
            "time": "2019.10",
            "value_avg": 0.48,
            "value_min": 0.21,
            "value_max": 2.7,
            "type": "primary"
          },
          {
            "time": "2019.10",
            "value_avg": 0.63,
            "value_min": 0.12,
            "value_max": 2,
            "type": "secondary"
          },
          {
            "time": "2019.11",
            "value_avg": 0.71,
            "value_min": 0.23,
            "value_max": 5.7,
            "type": "primary"
          },
          {
            "time": "2019.11",
            "value_avg": 0.99,
            "value_min": 0.45,
            "value_max": 5,
            "type": "secondary"
          },
          {
            "time": "2019.12",
            "value_avg": 0.97,
            "value_min": 0.37,
            "value_max": 6.06,
            "type": "primary"
          },
          {
            "time": "2019.12",
            "value_avg": 2.02,
            "value_min": 0.39,
            "value_max": 17.5,
            "type": "secondary"
          },
          {
            "time": "2020.01",
            "value_avg": 1.71,
            "value_min": 0.69,
            "value_max": 6.04,
            "type": "primary"
          },
          {
            "time": "2020.01",
            "value_avg": 2.97,
            "value_min": 0.55,
            "value_max": 20,
            "type": "secondary"
          },
          {
            "time": "2020.02",
            "value_avg": 2.15,
            "value_min": 1,
            "value_max": 6,
            "type": "primary"
          },
          {
            "time": "2020.02",
            "value_avg": 4.14,
            "value_min": 1,
            "value_max": 35,
            "type": "secondary"
          },
          {
            "time": "2020.03",
            "value_avg": 2.94,
            "value_min": 1.7,
            "value_max": 11.02,
            "type": "primary"
          },
          {
            "time": "2020.03",
            "value_avg": 3.94,
            "value_min": 1.7,
            "value_max": 10,
            "type": "secondary"
          },
          {
            "time": "2020.04",
            "value_avg": 3.63,
            "value_min": 2.31,
            "value_max": 11.1,
            "type": "primary"
          },
          {
            "time": "2020.04",
            "value_avg": 4.12,
            "value_min": 1.5,
            "value_max": 11.4,
            "type": "secondary"
          },
          {
            "time": "2020.05",
            "value_avg": 1.6,
            "value_min": 1.1,
            "value_max": 7,
            "type": "primary"
          },
          {
            "time": "2020.05",
            "value_avg": 3.2,
            "value_min": 1,
            "value_max": 10.14,
            "type": "secondary"
          },
          {
            "time": "2020.06",
            "value_avg": 1.36,
            "value_min": 1.01,
            "value_max": 3,
            "type": "primary"
          },
          {
            "time": "2020.06",
            "value_avg": 3.7,
            "value_min": 1.2,
            "value_max": 50,
            "type": "secondary"
          },
          {
            "time": "2020.07",
            "value_avg": 1.11,
            "value_min": 0.42,
            "value_max": 2.4,
            "type": "primary"
          },
          {
            "time": "2020.07",
            "value_avg": 2.72,
            "value_min": 0.7,
            "value_max": 14,
            "type": "secondary"
          },
          {
            "time": "2020.08",
            "value_avg": 0.84,
            "value_min": 0.2,
            "value_max": 2,
            "type": "primary"
          },
          {
            "time": "2020.08",
            "value_avg": 1.88,
            "value_min": 0.3,
            "value_max": 6.9,
            "type": "secondary"
          },
          {
            "time": "2020.09",
            "value_avg": 0.85,
            "value_min": 0.2,
            "value_max": 2.5,
            "type": "primary"
          },
          {
            "time": "2020.09",
            "value_avg": 2.12,
            "value_min": 0.6,
            "value_max": 14,
            "type": "secondary"
          },
          {
            "time": "2020.10",
            "value_avg": 1.39,
            "value_min": 0.23,
            "value_max": 4,
            "type": "primary"
          },
          {
            "time": "2020.10",
            "value_avg": 2.6,
            "value_min": 0.4,
            "value_max": 20,
            "type": "secondary"
          },
          {
            "time": "2020.11",
            "value_avg": 1.39,
            "value_min": 0.56,
            "value_max": 3.8,
            "type": "primary"
          },
          {
            "time": "2020.11",
            "value_avg": 2.28,
            "value_min": 0,
            "value_max": 11.5,
            "type": "secondary"
          },
          {
            "time": "2020.12",
            "value_avg": 0.79,
            "value_min": 0.4,
            "value_max": 2,
            "type": "primary"
          },
          {
            "time": "2020.12",
            "value_avg": 6.34,
            "value_min": 0.64,
            "value_max": 110,
            "type": "secondary"
          },
          {
            "time": "2021.01",
            "value_avg": 0.77,
            "value_min": 0.26,
            "value_max": 1.63,
            "type": "primary"
          },
          {
            "time": "2021.01",
            "value_avg": 1.59,
            "value_min": 0.43,
            "value_max": 4.45,
            "type": "secondary"
          },
          {
            "time": "2021.02",
            "value_avg": 1.06,
            "value_min": 0.5,
            "value_max": 3,
            "type": "primary"
          },
          {
            "time": "2021.02",
            "value_avg": 6.81,
            "value_min": 0.4,
            "value_max": 100,
            "type": "secondary"
          },
          {
            "time": "2021.03",
            "value_avg": 2,
            "value_min": 1,
            "value_max": 5.35,
            "type": "primary"
          },
          {
            "time": "2021.03",
            "value_avg": 3.75,
            "value_min": 0.75,
            "value_max": 22,
            "type": "secondary"
          },
          {
            "time": "2021.04",
            "value_avg": 2.05,
            "value_min": 1,
            "value_max": 5.47,
            "type": "primary"
          },
          {
            "time": "2021.04",
            "value_avg": 3.51,
            "value_min": 0.25,
            "value_max": 40,
            "type": "secondary"
          },
          {
            "time": "2021.05",
            "value_avg": 1.57,
            "value_min": 0.59,
            "value_max": 4.25,
            "type": "primary"
          },
          {
            "time": "2021.05",
            "value_avg": 2.48,
            "value_min": 0,
            "value_max": 10,
            "type": "secondary"
          },
          {
            "time": "2021.06",
            "value_avg": 1.83,
            "value_min": 0.75,
            "value_max": 4.22,
            "type": "primary"
          },
          {
            "time": "2021.06",
            "value_avg": 2.27,
            "value_min": 0.92,
            "value_max": 9.5,
            "type": "secondary"
          },
          {
            "time": "2021.07",
            "value_avg": 1.7,
            "value_min": 0.77,
            "value_max": 3.29,
            "type": "primary"
          },
          {
            "time": "2021.07",
            "value_avg": 2.47,
            "value_min": 0.96,
            "value_max": 7,
            "type": "secondary"
          },
          {
            "time": "2021.08",
            "value_avg": 1.65,
            "value_min": 0.6,
            "value_max": 3.08,
            "type": "primary"
          },
          {
            "time": "2021.08",
            "value_avg": 2.75,
            "value_min": 0.3,
            "value_max": 25,
            "type": "secondary"
          },
          {
            "time": "2021.09",
            "value_avg": 1.94,
            "value_min": 0.93,
            "value_max": 3.98,
            "type": "primary"
          },
          {
            "time": "2021.09",
            "value_avg": 2.4,
            "value_min": 0.95,
            "value_max": 8,
            "type": "secondary"
          },
          {
            "time": "2021.10",
            "value_avg": 1.54,
            "value_min": 0.98,
            "value_max": 2.8,
            "type": "primary"
          },
          {
            "time": "2021.10",
            "value_avg": 2.86,
            "value_min": 0.92,
            "value_max": 65,
            "type": "secondary"
          },
          {
            "time": "2021.11",
            "value_avg": 1.56,
            "value_min": 0.81,
            "value_max": 4.63,
            "type": "primary"
          },
          {
            "time": "2021.11",
            "value_avg": 3.15,
            "value_min": 0.95,
            "value_max": 20,
            "type": "secondary"
          },
          {
            "time": "2021.12",
            "value_avg": 2.17,
            "value_min": 1.26,
            "value_max": 6.15,
            "type": "primary"
          },
          {
            "time": "2021.12",
            "value_avg": 3.16,
            "value_min": 0,
            "value_max": 12.9,
            "type": "secondary"
          },
          {
            "time": "2022.01",
            "value_avg": 2.34,
            "value_min": 1.36,
            "value_max": 6.98,
            "type": "primary"
          },
          {
            "time": "2022.01",
            "value_avg": 3.25,
            "value_min": 0.5,
            "value_max": 20,
            "type": "secondary"
          },
          {
            "time": "2022.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          }
        ],
        "usd": [
          {
            "time": "2019.09",
            "value_avg": 88,
            "value_min": 42,
            "value_max": 213,
            "type": "primary"
          },
          {
            "time": "2019.09",
            "value_avg": 196,
            "value_min": 72,
            "value_max": 1219,
            "type": "secondary"
          },
          {
            "time": "2019.10",
            "value_avg": 85,
            "value_min": 33,
            "value_max": 514,
            "type": "primary"
          },
          {
            "time": "2019.10",
            "value_avg": 115,
            "value_min": 21,
            "value_max": 362,
            "type": "secondary"
          },
          {
            "time": "2019.11",
            "value_avg": 115,
            "value_min": 42,
            "value_max": 799,
            "type": "primary"
          },
          {
            "time": "2019.11",
            "value_avg": 170,
            "value_min": 66,
            "value_max": 956,
            "type": "secondary"
          },
          {
            "time": "2019.12",
            "value_avg": 127,
            "value_min": 53,
            "value_max": 757,
            "type": "primary"
          },
          {
            "time": "2019.12",
            "value_avg": 272,
            "value_min": 57,
            "value_max": 2244,
            "type": "secondary"
          },
          {
            "time": "2020.01",
            "value_avg": 272,
            "value_min": 90,
            "value_max": 1054,
            "type": "primary"
          },
          {
            "time": "2020.01",
            "value_avg": 449,
            "value_min": 91,
            "value_max": 2674,
            "type": "secondary"
          },
          {
            "time": "2020.02",
            "value_avg": 514,
            "value_min": 236,
            "value_max": 1489,
            "type": "primary"
          },
          {
            "time": "2020.02",
            "value_avg": 914,
            "value_min": 215,
            "value_max": 7135,
            "type": "secondary"
          },
          {
            "time": "2020.03",
            "value_avg": 488,
            "value_min": 187,
            "value_max": 2069,
            "type": "primary"
          },
          {
            "time": "2020.03",
            "value_avg": 660,
            "value_min": 249,
            "value_max": 2183,
            "type": "secondary"
          },
          {
            "time": "2020.04",
            "value_avg": 536,
            "value_min": 314,
            "value_max": 1478,
            "type": "primary"
          },
          {
            "time": "2020.04",
            "value_avg": 687,
            "value_min": 255,
            "value_max": 1804,
            "type": "secondary"
          },
          {
            "time": "2020.05",
            "value_avg": 326,
            "value_min": 208,
            "value_max": 1443,
            "type": "primary"
          },
          {
            "time": "2020.05",
            "value_avg": 659,
            "value_min": 213,
            "value_max": 2148,
            "type": "secondary"
          },
          {
            "time": "2020.06",
            "value_avg": 326,
            "value_min": 234,
            "value_max": 711,
            "type": "primary"
          },
          {
            "time": "2020.06",
            "value_avg": 878,
            "value_min": 280,
            "value_max": 11584,
            "type": "secondary"
          },
          {
            "time": "2020.07",
            "value_avg": 271,
            "value_min": 101,
            "value_max": 759,
            "type": "primary"
          },
          {
            "time": "2020.07",
            "value_avg": 711,
            "value_min": 222,
            "value_max": 3355,
            "type": "secondary"
          },
          {
            "time": "2020.08",
            "value_avg": 334,
            "value_min": 83,
            "value_max": 771,
            "type": "primary"
          },
          {
            "time": "2020.08",
            "value_avg": 751,
            "value_min": 115,
            "value_max": 2669,
            "type": "secondary"
          },
          {
            "time": "2020.09",
            "value_avg": 305,
            "value_min": 68,
            "value_max": 898,
            "type": "primary"
          },
          {
            "time": "2020.09",
            "value_avg": 771,
            "value_min": 215,
            "value_max": 4962,
            "type": "secondary"
          },
          {
            "time": "2020.10",
            "value_avg": 523,
            "value_min": 79,
            "value_max": 1555,
            "type": "primary"
          },
          {
            "time": "2020.10",
            "value_avg": 955,
            "value_min": 138,
            "value_max": 7191,
            "type": "secondary"
          },
          {
            "time": "2020.11",
            "value_avg": 628,
            "value_min": 266,
            "value_max": 1526,
            "type": "primary"
          },
          {
            "time": "2020.11",
            "value_avg": 1049,
            "value_min": 0,
            "value_max": 5488,
            "type": "secondary"
          },
          {
            "time": "2020.12",
            "value_avg": 467,
            "value_min": 236,
            "value_max": 1197,
            "type": "primary"
          },
          {
            "time": "2020.12",
            "value_avg": 4020,
            "value_min": 380,
            "value_max": 70346,
            "type": "secondary"
          },
          {
            "time": "2021.01",
            "value_avg": 996,
            "value_min": 364,
            "value_max": 2255,
            "type": "primary"
          },
          {
            "time": "2021.01",
            "value_avg": 1901,
            "value_min": 574,
            "value_max": 6107,
            "type": "secondary"
          },
          {
            "time": "2021.02",
            "value_avg": 1817,
            "value_min": 862,
            "value_max": 5909,
            "type": "primary"
          },
          {
            "time": "2021.02",
            "value_avg": 11762,
            "value_min": 658,
            "value_max": 184557,
            "type": "secondary"
          },
          {
            "time": "2021.03",
            "value_avg": 3454,
            "value_min": 1497,
            "value_max": 9720,
            "type": "primary"
          },
          {
            "time": "2021.03",
            "value_avg": 6538,
            "value_min": 1177,
            "value_max": 39163,
            "type": "secondary"
          },
          {
            "time": "2021.04",
            "value_avg": 4564,
            "value_min": 2298,
            "value_max": 12437,
            "type": "primary"
          },
          {
            "time": "2021.04",
            "value_avg": 7763,
            "value_min": 633,
            "value_max": 84602,
            "type": "secondary"
          },
          {
            "time": "2021.05",
            "value_avg": 4874,
            "value_min": 1428,
            "value_max": 13376,
            "type": "primary"
          },
          {
            "time": "2021.05",
            "value_avg": 7898,
            "value_min": 0,
            "value_max": 23063,
            "type": "secondary"
          },
          {
            "time": "2021.06",
            "value_avg": 4201,
            "value_min": 1833,
            "value_max": 7739,
            "type": "primary"
          },
          {
            "time": "2021.06",
            "value_avg": 5395,
            "value_min": 1919,
            "value_max": 24515,
            "type": "secondary"
          },
          {
            "time": "2021.07",
            "value_avg": 3641,
            "value_min": 1448,
            "value_max": 6892,
            "type": "primary"
          },
          {
            "time": "2021.07",
            "value_avg": 5274,
            "value_min": 1923,
            "value_max": 16097,
            "type": "secondary"
          },
          {
            "time": "2021.08",
            "value_avg": 4904,
            "value_min": 1718,
            "value_max": 9949,
            "type": "primary"
          },
          {
            "time": "2021.08",
            "value_avg": 8420,
            "value_min": 817,
            "value_max": 65291,
            "type": "secondary"
          },
          {
            "time": "2021.09",
            "value_avg": 6471,
            "value_min": 2925,
            "value_max": 12330,
            "type": "primary"
          },
          {
            "time": "2021.09",
            "value_avg": 8347,
            "value_min": 2780,
            "value_max": 23517,
            "type": "secondary"
          },
          {
            "time": "2021.10",
            "value_avg": 5840,
            "value_min": 3431,
            "value_max": 10142,
            "type": "primary"
          },
          {
            "time": "2021.10",
            "value_avg": 11026,
            "value_min": 3296,
            "value_max": 264865,
            "type": "secondary"
          },
          {
            "time": "2021.11",
            "value_avg": 6905,
            "value_min": 3799,
            "value_max": 20578,
            "type": "primary"
          },
          {
            "time": "2021.11",
            "value_avg": 14056,
            "value_min": 4309,
            "value_max": 93058,
            "type": "secondary"
          },
          {
            "time": "2021.12",
            "value_avg": 9198,
            "value_min": 4865,
            "value_max": 26750,
            "type": "primary"
          },
          {
            "time": "2021.12",
            "value_avg": 13480,
            "value_min": 3,
            "value_max": 59205,
            "type": "secondary"
          },
          {
            "time": "2022.01",
            "value_avg": 6843,
            "value_min": 3378,
            "value_max": 23571,
            "type": "primary"
          },
          {
            "time": "2022.01",
            "value_avg": 10298,
            "value_min": 1556,
            "value_max": 68336,
            "type": "secondary"
          },
          {
            "time": "2022.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "primary"
          },
          {
            "time": "2022.02",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "secondary"
          }
        ]
      }
    }
  }
}

```
---
**6\.4 获取 Cryptovoxels 地块成交总数量统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 地块成交总数量统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_sold_total_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "daily": {
      "data": [
        {
          "time": "01.24",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "01.24",
          "value": 6,
          "type": "secondary"
        },
        {
          "time": "01.25",
          "value": 17,
          "type": "primary"
        },
        {
          "time": "01.25",
          "value": 7,
          "type": "secondary"
        },
        {
          "time": "01.26",
          "value": 27,
          "type": "primary"
        },
        {
          "time": "01.26",
          "value": 9,
          "type": "secondary"
        },
        {
          "time": "01.27",
          "value": 13,
          "type": "primary"
        },
        {
          "time": "01.27",
          "value": 7,
          "type": "secondary"
        },
        {
          "time": "01.28",
          "value": 19,
          "type": "primary"
        },
        {
          "time": "01.28",
          "value": 4,
          "type": "secondary"
        },
        {
          "time": "01.29",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "01.29",
          "value": 2,
          "type": "secondary"
        },
        {
          "time": "01.30",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "01.30",
          "value": 3,
          "type": "secondary"
        },
        {
          "time": "01.31",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "01.31",
          "value": 2,
          "type": "secondary"
        },
        {
          "time": "02.01",
          "value": 4,
          "type": "primary"
        },
        {
          "time": "02.01",
          "value": 3,
          "type": "secondary"
        },
        {
          "time": "02.02",
          "value": 35,
          "type": "primary"
        },
        {
          "time": "02.02",
          "value": 6,
          "type": "secondary"
        },
        {
          "time": "02.03",
          "value": 10,
          "type": "primary"
        },
        {
          "time": "02.03",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.04",
          "value": 21,
          "type": "primary"
        },
        {
          "time": "02.04",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.05",
          "value": 11,
          "type": "primary"
        },
        {
          "time": "02.05",
          "value": 7,
          "type": "secondary"
        },
        {
          "time": "02.06",
          "value": 3,
          "type": "primary"
        },
        {
          "time": "02.06",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.07",
          "value": 4,
          "type": "primary"
        },
        {
          "time": "02.07",
          "value": 7,
          "type": "secondary"
        },
        {
          "time": "02.08",
          "value": 4,
          "type": "primary"
        },
        {
          "time": "02.08",
          "value": 4,
          "type": "secondary"
        },
        {
          "time": "02.09",
          "value": 31,
          "type": "primary"
        },
        {
          "time": "02.09",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.10",
          "value": 5,
          "type": "primary"
        },
        {
          "time": "02.10",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.11",
          "value": 12,
          "type": "primary"
        },
        {
          "time": "02.11",
          "value": 2,
          "type": "secondary"
        },
        {
          "time": "02.12",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.12",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.13",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.13",
          "value": 6,
          "type": "secondary"
        },
        {
          "time": "02.14",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.14",
          "value": 1,
          "type": "secondary"
        },
        {
          "time": "02.15",
          "value": 4,
          "type": "primary"
        },
        {
          "time": "02.15",
          "value": 2,
          "type": "secondary"
        },
        {
          "time": "02.16",
          "value": 14,
          "type": "primary"
        },
        {
          "time": "02.16",
          "value": 2,
          "type": "secondary"
        },
        {
          "time": "02.17",
          "value": 19,
          "type": "primary"
        },
        {
          "time": "02.17",
          "value": 8,
          "type": "secondary"
        },
        {
          "time": "02.18",
          "value": 16,
          "type": "primary"
        },
        {
          "time": "02.18",
          "value": 5,
          "type": "secondary"
        },
        {
          "time": "02.19",
          "value": 8,
          "type": "primary"
        },
        {
          "time": "02.19",
          "value": 11,
          "type": "secondary"
        },
        {
          "time": "02.20",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.20",
          "value": 0,
          "type": "secondary"
        },
        {
          "time": "02.21",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.21",
          "value": 0,
          "type": "secondary"
        },
        {
          "time": "02.22",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "02.22",
          "value": 0,
          "type": "secondary"
        }
      ]
    },
    "monthly": {
      "data": [
        {
          "time": "2019.09",
          "value": 152,
          "type": "primary"
        },
        {
          "time": "2019.09",
          "value": 27,
          "type": "secondary"
        },
        {
          "time": "2019.10",
          "value": 153,
          "type": "primary"
        },
        {
          "time": "2019.10",
          "value": 21,
          "type": "secondary"
        },
        {
          "time": "2019.11",
          "value": 166,
          "type": "primary"
        },
        {
          "time": "2019.11",
          "value": 31,
          "type": "secondary"
        },
        {
          "time": "2019.12",
          "value": 188,
          "type": "primary"
        },
        {
          "time": "2019.12",
          "value": 97,
          "type": "secondary"
        },
        {
          "time": "2020.01",
          "value": 381,
          "type": "primary"
        },
        {
          "time": "2020.01",
          "value": 133,
          "type": "secondary"
        },
        {
          "time": "2020.02",
          "value": 262,
          "type": "primary"
        },
        {
          "time": "2020.02",
          "value": 140,
          "type": "secondary"
        },
        {
          "time": "2020.03",
          "value": 243,
          "type": "primary"
        },
        {
          "time": "2020.03",
          "value": 180,
          "type": "secondary"
        },
        {
          "time": "2020.04",
          "value": 125,
          "type": "primary"
        },
        {
          "time": "2020.04",
          "value": 114,
          "type": "secondary"
        },
        {
          "time": "2020.05",
          "value": 180,
          "type": "primary"
        },
        {
          "time": "2020.05",
          "value": 109,
          "type": "secondary"
        },
        {
          "time": "2020.06",
          "value": 233,
          "type": "primary"
        },
        {
          "time": "2020.06",
          "value": 158,
          "type": "secondary"
        },
        {
          "time": "2020.07",
          "value": 159,
          "type": "primary"
        },
        {
          "time": "2020.07",
          "value": 81,
          "type": "secondary"
        },
        {
          "time": "2020.08",
          "value": 62,
          "type": "primary"
        },
        {
          "time": "2020.08",
          "value": 66,
          "type": "secondary"
        },
        {
          "time": "2020.09",
          "value": 184,
          "type": "primary"
        },
        {
          "time": "2020.09",
          "value": 77,
          "type": "secondary"
        },
        {
          "time": "2020.10",
          "value": 153,
          "type": "primary"
        },
        {
          "time": "2020.10",
          "value": 172,
          "type": "secondary"
        },
        {
          "time": "2020.11",
          "value": 159,
          "type": "primary"
        },
        {
          "time": "2020.11",
          "value": 59,
          "type": "secondary"
        },
        {
          "time": "2020.12",
          "value": 40,
          "type": "primary"
        },
        {
          "time": "2020.12",
          "value": 43,
          "type": "secondary"
        },
        {
          "time": "2021.01",
          "value": 42,
          "type": "primary"
        },
        {
          "time": "2021.01",
          "value": 46,
          "type": "secondary"
        },
        {
          "time": "2021.02",
          "value": 87,
          "type": "primary"
        },
        {
          "time": "2021.02",
          "value": 97,
          "type": "secondary"
        },
        {
          "time": "2021.03",
          "value": 158,
          "type": "primary"
        },
        {
          "time": "2021.03",
          "value": 174,
          "type": "secondary"
        },
        {
          "time": "2021.04",
          "value": 190,
          "type": "primary"
        },
        {
          "time": "2021.04",
          "value": 147,
          "type": "secondary"
        },
        {
          "time": "2021.05",
          "value": 164,
          "type": "primary"
        },
        {
          "time": "2021.05",
          "value": 106,
          "type": "secondary"
        },
        {
          "time": "2021.06",
          "value": 103,
          "type": "primary"
        },
        {
          "time": "2021.06",
          "value": 99,
          "type": "secondary"
        },
        {
          "time": "2021.07",
          "value": 244,
          "type": "primary"
        },
        {
          "time": "2021.07",
          "value": 153,
          "type": "secondary"
        },
        {
          "time": "2021.08",
          "value": 217,
          "type": "primary"
        },
        {
          "time": "2021.08",
          "value": 225,
          "type": "secondary"
        },
        {
          "time": "2021.09",
          "value": 215,
          "type": "primary"
        },
        {
          "time": "2021.09",
          "value": 148,
          "type": "secondary"
        },
        {
          "time": "2021.10",
          "value": 177,
          "type": "primary"
        },
        {
          "time": "2021.10",
          "value": 133,
          "type": "secondary"
        },
        {
          "time": "2021.11",
          "value": 360,
          "type": "primary"
        },
        {
          "time": "2021.11",
          "value": 261,
          "type": "secondary"
        },
        {
          "time": "2021.12",
          "value": 217,
          "type": "primary"
        },
        {
          "time": "2021.12",
          "value": 230,
          "type": "secondary"
        },
        {
          "time": "2022.01",
          "value": 165,
          "type": "primary"
        },
        {
          "time": "2022.01",
          "value": 157,
          "type": "secondary"
        },
        {
          "time": "2022.02",
          "value": 201,
          "type": "primary"
        },
        {
          "time": "2022.02",
          "value": 94,
          "type": "secondary"
        }
      ]
    }
  }
}
```
---
**6\.5 获取 Cryptovoxels 地块销售总额统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 地块销售总额统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_sold_sum_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "eth": {
      "data": [
        {
          "time": "2019-09",
          "value": 75.35,
          "type": "primary"
        },
        {
          "time": "2019-10",
          "value": 72.88,
          "type": "primary"
        },
        {
          "time": "2019-11",
          "value": 117.86,
          "type": "primary"
        },
        {
          "time": "2019-12",
          "value": 182.5,
          "type": "primary"
        },
        {
          "time": "2020-01",
          "value": 661.65,
          "type": "primary"
        },
        {
          "time": "2020-02",
          "value": 565.13,
          "type": "primary"
        },
        {
          "time": "2020-03",
          "value": 719.86,
          "type": "primary"
        },
        {
          "time": "2020-04",
          "value": 453.54,
          "type": "primary"
        },
        {
          "time": "2020-05",
          "value": 287.83,
          "type": "primary"
        },
        {
          "time": "2020-06",
          "value": 316.67,
          "type": "primary"
        },
        {
          "time": "2020-07",
          "value": 176,
          "type": "primary"
        },
        {
          "time": "2020-08",
          "value": 52.01,
          "type": "primary"
        },
        {
          "time": "2020-09",
          "value": 157.47,
          "type": "primary"
        },
        {
          "time": "2020-10",
          "value": 216.14,
          "type": "primary"
        },
        {
          "time": "2020-11",
          "value": 222.39,
          "type": "primary"
        },
        {
          "time": "2020-12",
          "value": 31.41,
          "type": "primary"
        },
        {
          "time": "2021-01",
          "value": 32.37,
          "type": "primary"
        },
        {
          "time": "2021-02",
          "value": 92.45,
          "type": "primary"
        },
        {
          "time": "2021-03",
          "value": 314.02,
          "type": "primary"
        },
        {
          "time": "2021-04",
          "value": 388.78,
          "type": "primary"
        },
        {
          "time": "2021-05",
          "value": 257.74,
          "type": "primary"
        },
        {
          "time": "2021-06",
          "value": 188.8,
          "type": "primary"
        },
        {
          "time": "2021-07",
          "value": 414.4,
          "type": "primary"
        },
        {
          "time": "2021-08",
          "value": 358.63,
          "type": "primary"
        },
        {
          "time": "2021-09",
          "value": 416.27,
          "type": "primary"
        },
        {
          "time": "2021-10",
          "value": 272.36,
          "type": "primary"
        },
        {
          "time": "2021-11",
          "value": 562.06,
          "type": "primary"
        },
        {
          "time": "2021-12",
          "value": 470.42,
          "type": "primary"
        },
        {
          "time": "2022-01",
          "value": 381.64,
          "type": "primary"
        },
        {
          "time": "2022-02",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "2019-09",
          "value": 27.28,
          "type": "secondary"
        },
        {
          "time": "2019-10",
          "value": 13.92,
          "type": "secondary"
        },
        {
          "time": "2019-11",
          "value": 30.83,
          "type": "secondary"
        },
        {
          "time": "2019-12",
          "value": 197.75,
          "type": "secondary"
        },
        {
          "time": "2020-01",
          "value": 394.61,
          "type": "secondary"
        },
        {
          "time": "2020-02",
          "value": 587.78,
          "type": "secondary"
        },
        {
          "time": "2020-03",
          "value": 705.12,
          "type": "secondary"
        },
        {
          "time": "2020-04",
          "value": 470.11,
          "type": "secondary"
        },
        {
          "time": "2020-05",
          "value": 345.94,
          "type": "secondary"
        },
        {
          "time": "2020-06",
          "value": 584.92,
          "type": "secondary"
        },
        {
          "time": "2020-07",
          "value": 220.02,
          "type": "secondary"
        },
        {
          "time": "2020-08",
          "value": 125.97,
          "type": "secondary"
        },
        {
          "time": "2020-09",
          "value": 165.32,
          "type": "secondary"
        },
        {
          "time": "2020-10",
          "value": 454.99,
          "type": "secondary"
        },
        {
          "time": "2020-11",
          "value": 139.14,
          "type": "secondary"
        },
        {
          "time": "2020-12",
          "value": 272.62,
          "type": "secondary"
        },
        {
          "time": "2021-01",
          "value": 72.98,
          "type": "secondary"
        },
        {
          "time": "2021-02",
          "value": 660.45,
          "type": "secondary"
        },
        {
          "time": "2021-03",
          "value": 651.88,
          "type": "secondary"
        },
        {
          "time": "2021-04",
          "value": 516.34,
          "type": "secondary"
        },
        {
          "time": "2021-05",
          "value": 267.79,
          "type": "secondary"
        },
        {
          "time": "2021-06",
          "value": 224.55,
          "type": "secondary"
        },
        {
          "time": "2021-07",
          "value": 380.39,
          "type": "secondary"
        },
        {
          "time": "2021-08",
          "value": 620.89,
          "type": "secondary"
        },
        {
          "time": "2021-09",
          "value": 357.05,
          "type": "secondary"
        },
        {
          "time": "2021-10",
          "value": 386.33,
          "type": "secondary"
        },
        {
          "time": "2021-11",
          "value": 821.69,
          "type": "secondary"
        },
        {
          "time": "2021-12",
          "value": 727.48,
          "type": "secondary"
        },
        {
          "time": "2022-01",
          "value": 486.87,
          "type": "secondary"
        },
        {
          "time": "2022-02",
          "value": 0,
          "type": "secondary"
        }
      ]
    },
    "usd": {
      "data": [
        {
          "time": "2019-09",
          "value": 13683,
          "type": "primary"
        },
        {
          "time": "2019-10",
          "value": 13119,
          "type": "primary"
        },
        {
          "time": "2019-11",
          "value": 19139,
          "type": "primary"
        },
        {
          "time": "2019-12",
          "value": 24094,
          "type": "primary"
        },
        {
          "time": "2020-01",
          "value": 105358,
          "type": "primary"
        },
        {
          "time": "2020-02",
          "value": 135408,
          "type": "primary"
        },
        {
          "time": "2020-03",
          "value": 119695,
          "type": "primary"
        },
        {
          "time": "2020-04",
          "value": 67057,
          "type": "primary"
        },
        {
          "time": "2020-05",
          "value": 58761,
          "type": "primary"
        },
        {
          "time": "2020-06",
          "value": 76012,
          "type": "primary"
        },
        {
          "time": "2020-07",
          "value": 42962,
          "type": "primary"
        },
        {
          "time": "2020-08",
          "value": 20745,
          "type": "primary"
        },
        {
          "time": "2020-09",
          "value": 56740,
          "type": "primary"
        },
        {
          "time": "2020-10",
          "value": 81136,
          "type": "primary"
        },
        {
          "time": "2020-11",
          "value": 100556,
          "type": "primary"
        },
        {
          "time": "2020-12",
          "value": 18719,
          "type": "primary"
        },
        {
          "time": "2021-01",
          "value": 41841,
          "type": "primary"
        },
        {
          "time": "2021-02",
          "value": 158155,
          "type": "primary"
        },
        {
          "time": "2021-03",
          "value": 542351,
          "type": "primary"
        },
        {
          "time": "2021-04",
          "value": 867335,
          "type": "primary"
        },
        {
          "time": "2021-05",
          "value": 799482,
          "type": "primary"
        },
        {
          "time": "2021-06",
          "value": 432717,
          "type": "primary"
        },
        {
          "time": "2021-07",
          "value": 888565,
          "type": "primary"
        },
        {
          "time": "2021-08",
          "value": 1064215,
          "type": "primary"
        },
        {
          "time": "2021-09",
          "value": 1391441,
          "type": "primary"
        },
        {
          "time": "2021-10",
          "value": 1033794,
          "type": "primary"
        },
        {
          "time": "2021-11",
          "value": 2486111,
          "type": "primary"
        },
        {
          "time": "2021-12",
          "value": 1996087,
          "type": "primary"
        },
        {
          "time": "2022-01",
          "value": 1115463,
          "type": "primary"
        },
        {
          "time": "2022-02",
          "value": 0,
          "type": "primary"
        },
        {
          "time": "2019-09",
          "value": 5504,
          "type": "secondary"
        },
        {
          "time": "2019-10",
          "value": 2543,
          "type": "secondary"
        },
        {
          "time": "2019-11",
          "value": 5284,
          "type": "secondary"
        },
        {
          "time": "2019-12",
          "value": 26676,
          "type": "secondary"
        },
        {
          "time": "2020-01",
          "value": 59774,
          "type": "secondary"
        },
        {
          "time": "2020-02",
          "value": 129842,
          "type": "secondary"
        },
        {
          "time": "2020-03",
          "value": 118157,
          "type": "secondary"
        },
        {
          "time": "2020-04",
          "value": 78413,
          "type": "secondary"
        },
        {
          "time": "2020-05",
          "value": 71245,
          "type": "secondary"
        },
        {
          "time": "2020-06",
          "value": 138874,
          "type": "secondary"
        },
        {
          "time": "2020-07",
          "value": 57591,
          "type": "secondary"
        },
        {
          "time": "2020-08",
          "value": 50337,
          "type": "secondary"
        },
        {
          "time": "2020-09",
          "value": 60210,
          "type": "secondary"
        },
        {
          "time": "2020-10",
          "value": 167136,
          "type": "secondary"
        },
        {
          "time": "2020-11",
          "value": 63993,
          "type": "secondary"
        },
        {
          "time": "2020-12",
          "value": 172874,
          "type": "secondary"
        },
        {
          "time": "2021-01",
          "value": 87466,
          "type": "secondary"
        },
        {
          "time": "2021-02",
          "value": 1140946,
          "type": "secondary"
        },
        {
          "time": "2021-03",
          "value": 1137707,
          "type": "secondary"
        },
        {
          "time": "2021-04",
          "value": 1141304,
          "type": "secondary"
        },
        {
          "time": "2021-05",
          "value": 853028,
          "type": "secondary"
        },
        {
          "time": "2021-06",
          "value": 534176,
          "type": "secondary"
        },
        {
          "time": "2021-07",
          "value": 812291,
          "type": "secondary"
        },
        {
          "time": "2021-08",
          "value": 1902969,
          "type": "secondary"
        },
        {
          "time": "2021-09",
          "value": 1243782,
          "type": "secondary"
        },
        {
          "time": "2021-10",
          "value": 1488606,
          "type": "secondary"
        },
        {
          "time": "2021-11",
          "value": 3668753,
          "type": "secondary"
        },
        {
          "time": "2021-12",
          "value": 3100435,
          "type": "secondary"
        },
        {
          "time": "2022-01",
          "value": 1544749,
          "type": "secondary"
        },
        {
          "time": "2022-02",
          "value": 0,
          "type": "secondary"
        }
      ]
    }
  }
}
```
---
**6\.6 获取 Cryptovoxels 地块mint情况统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 地块mint情况统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_mint_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "monthly": {
      "data": [
        {
          "time": "2019.09",
          "value": 214,
          "type": "all"
        },
        {
          "time": "2019.10",
          "value": 155,
          "type": "all"
        },
        {
          "time": "2019.11",
          "value": 92,
          "type": "all"
        },
        {
          "time": "2019.12",
          "value": 249,
          "type": "all"
        },
        {
          "time": "2020.01",
          "value": 399,
          "type": "all"
        },
        {
          "time": "2020.02",
          "value": 267,
          "type": "all"
        },
        {
          "time": "2020.03",
          "value": 282,
          "type": "all"
        },
        {
          "time": "2020.04",
          "value": 38,
          "type": "all"
        },
        {
          "time": "2020.05",
          "value": 183,
          "type": "all"
        },
        {
          "time": "2020.06",
          "value": 285,
          "type": "all"
        },
        {
          "time": "2020.07",
          "value": 144,
          "type": "all"
        },
        {
          "time": "2020.08",
          "value": 46,
          "type": "all"
        },
        {
          "time": "2020.09",
          "value": 206,
          "type": "all"
        },
        {
          "time": "2020.10",
          "value": 139,
          "type": "all"
        },
        {
          "time": "2020.11",
          "value": 195,
          "type": "all"
        },
        {
          "time": "2020.12",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.01",
          "value": 43,
          "type": "all"
        },
        {
          "time": "2021.02",
          "value": 102,
          "type": "all"
        },
        {
          "time": "2021.03",
          "value": 206,
          "type": "all"
        },
        {
          "time": "2021.04",
          "value": 186,
          "type": "all"
        },
        {
          "time": "2021.05",
          "value": 154,
          "type": "all"
        },
        {
          "time": "2021.06",
          "value": 63,
          "type": "all"
        },
        {
          "time": "2021.07",
          "value": 273,
          "type": "all"
        },
        {
          "time": "2021.08",
          "value": 272,
          "type": "all"
        },
        {
          "time": "2021.09",
          "value": 232,
          "type": "all"
        },
        {
          "time": "2021.10",
          "value": 233,
          "type": "all"
        },
        {
          "time": "2021.11",
          "value": 557,
          "type": "all"
        },
        {
          "time": "2021.12",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2022.01",
          "value": 402,
          "type": "all"
        },
        {
          "time": "2022.02",
          "value": 395,
          "type": "all"
        }
      ]
    }
  }
}
```
---
**6\.7 获取 Cryptovoxels 地主总数统计信息接口**
###### 接口功能
> 获取 Cryptovoxels 地主总数统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_cv_parcel_owner_stats

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 返回字段
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "monthly": {
      "data": [
        {
          "time": "2021.07",
          "value": 1396,
          "type": "all"
        },
        {
          "time": "2021.08",
          "value": 1470,
          "type": "all"
        },
        {
          "time": "2021.09",
          "value": 1539,
          "type": "all"
        },
        {
          "time": "2021.10",
          "value": 1617,
          "type": "all"
        },
        {
          "time": "2021.11",
          "value": 1812,
          "type": "all"
        },
        {
          "time": "2021.12",
          "value": 1945,
          "type": "all"
        },
        {
          "time": "2022.01",
          "value": 2054,
          "type": "all"
        },
        {
          "time": "2022.02",
          "value": 2149,
          "type": "all"
        }
      ]
    }
  }
}
```