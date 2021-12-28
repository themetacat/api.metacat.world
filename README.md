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
| data.list.img_url_list     | string   | topic封面图，4张小图对应的url    |

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
