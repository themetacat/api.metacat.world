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
3.  获取 Decentraland 第三级地图数据
4.  获取 Decentraland 地图的 Land 详细信息

### 六、Metaverse Analytics 相关接口
1. 获取各元宇宙平台概要信息接口
2. 获取 Cryptovoxels 流量统计信息接口
3. 获取 Cryptovoxels 地块成交均价统计信息接口
4. 获取 Cryptovoxels 地块成交总数量统计信息接口
5. 获取 Cryptovoxels 地块销售总额统计信息接口
6. 获取 Cryptovoxels 地块mint情况统计信息接口
7. 获取 Cryptovoxels 地主总数统计信息接口
8. 获取 Decentraland 地块成交均价统计信息接口
9. 获取 Decentraland 地块成交总数量统计信息接口
10. 获取 Decentraland 地块销售总额统计信息接口
11. 获取 Decentraland 地主总数统计信息接口

### 七、用户登录相关接口
1. 获取钱包登录所需 nonce 接口
2. 用户登录接口
3. 用户登出接口
4. 用户 access_token 刷新接口
5. 获取当前登录者基本信息接口
6. 更新当前登录者基本信息接口
7. 获取当前登录者地块列表接口
8. 判断 nick_name 是否已存在的接口

### 八、虚拟土地租赁相关接口
1. 获取当前登录者 Cryptovoxels 地块列表接口
2. 批量（单个）挂出 Cryptovoxels 待租地块接口
3. 批量（单个）取消已挂出 Cryptovoxels 地块接口
4. 批量（单个）更新已挂出 Cryptovoxels 地块为租赁中接口
5. 单个更新 Cryptovoxels 地块租赁信息接口
6. 获取 Cryptovoxels 岛屿列表接口
7. 单个更新租赁中 Cryptovoxels 地块为已挂出状态接口

### 九、Wearable 相关接口
1. 获取 OKX Wearable 列表页数据接口
2. 获取 OKX Wearable 详情页数据接口 

----
## 全局错误码

|  Code  | Description                                | Oher                               |
| :----: | :----------------------------------------- | :--------------------------------- |
| 100000 | success                                    |                                    |
| 100001 | param error                                |                                    |
| 100002 | signature verify failed                    |                                    |
| 100003 | please login first                         | refresh_token 过期，请重新登录        |
| 100004 | update failed                              |                                    |
| 100005 | system error, please retry                 |                                    |
| 100006 | nick_name exist                            |                                    |
| 100007 | email exist                                |                                    |
| 100008 | user not exist                             |  用户不存在                          |
| 100009 | twitter_name exist                         |                                    |
| 100010 | parcel not yours                           |       地块不属于当前用户              |

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
**5\.3 获取 Decentraland 第三级地图数据**
###### 接口功能
> 获取 Decentraland 第三级地图数据接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_price_map_level_three

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| -  | - | -  | -    | -  |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_dcl_price_map_level_three' | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "stats": {
      "price": {
        "level_one": [
          {
            "month": {
              "start": 74112,
              "end": 18437
            },
            "quarter": {
              "start": 83778,
              "end": 22357
            },
            "year": {
              "start": 434811,
              "end": 21465
            },
            "all": {
              "start": 244168,
              "end": 18122
            }
          },
          {
            "month": {
              "start": 17807,
              "end": 14958
            },
            "quarter": {
              "start": 22262,
              "end": 18723
            },
            "year": {
              "start": 21411,
              "end": 17517
            },
            "all": {
              "start": 18112,
              "end": 14524
            }
          },
          {
            "month": {
              "start": 14947,
              "end": 14099
            },
            "quarter": {
              "start": 18676,
              "end": 17089
            },
            "year": {
              "start": 17515,
              "end": 15483
            },
            "all": {
              "start": 14514,
              "end": 11150
            }
          },
          {
            "month": {
              "start": 14091,
              "end": 13625
            },
            "quarter": {
              "start": 17051,
              "end": 15926
            },
            "year": {
              "start": 15476,
              "end": 13831
            },
            "all": {
              "start": 11142,
              "end": 7281
            }
          },
          {
            "month": {
              "start": 13594,
              "end": 13149
            },
            "quarter": {
              "start": 15908,
              "end": 14765
            },
            "year": {
              "start": 13826,
              "end": 11658
            },
            "all": {
              "start": 7273,
              "end": 5110
            }
          },
          {
            "month": {
              "start": 13134,
              "end": 12052
            },
            "quarter": {
              "start": 14764,
              "end": 13604
            },
            "year": {
              "start": 11653,
              "end": 7058
            },
            "all": {
              "start": 5097,
              "end": 2623
            }
          },
          {
            "month": {
              "start": 11984,
              "end": 9699
            },
            "quarter": {
              "start": 13594,
              "end": 11490
            },
            "year": {
              "start": 7057,
              "end": 4573
            },
            "all": {
              "start": 2618,
              "end": 1061
            }
          },
          {
            "month": {
              "start": 9681,
              "end": 0
            },
            "quarter": {
              "start": 11485,
              "end": 0
            },
            "year": {
              "start": 4572,
              "end": 0
            },
            "all": {
              "start": 1058,
              "end": 0
            }
          }
        ]
      }
    },
    "parcels": [
      {
        "properties": {
          "land_id": 1.157920892373162e+77,
          "id": "-150,150",
          "type": "district",
          "top": true,
          "left": false,
          "topLeft": false,
          "estate_id": "1186"
        },
        "price": {
          "month": 0,
          "quarter": 0,
          "year": 0,
          "all": 0
        }
      }
    ]
  }
}
```
---
**5\.4 获取 Decentraland 地图的 Land 详细信息**
###### 接口功能
> 获取 Decentraland 地图的 Land 详细信息接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_detail

###### 返回数据格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数  | 必选  | 类型 | 默认值 | 描述           |
| :---- | :---- | :--: | :----- | -------------- |
| land_id | True | string  | ''    | 地块id  |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/get_dcl_parcel_detail?land_id=115792089237316195423570985008687907802227629627499794519951392893147897921560' | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "land_id": "115792089237316195423570985008687907802227629627499794519951392893147897921560",
    "estate_id": 0,
    "name": "Fashion District Parcel (2)",
    "description": "Great Location",
    "cover_img_url": "https://api.decentraland.org/v2/parcels/-150/24/map.png",
    "opensea_url": "https://opensea.io/assets/0xf87e31492faf9a91b02ee0deaad50d51d56d5d4d/115792089237316195423570985008687907802227629627499794519951392893147897921560",
    "parcel_page_url": "https://market.decentraland.org/contracts/0xf87e31492faf9a91b02ee0deaad50d51d56d5d4d/tokens/115792089237316195423570985008687907802227629627499794519951392893147897921560",
    "time_range_sale": {
      "mana": 129137,
      "usd": 25463.78
    },
    "last_sale_list": [
      {
        "date": "2021.11.14",
        "mana": 5222,
        "usd": 17004.55,
        "is_primary": 0
      },
      {
        "date": "2018.12.11",
        "mana": 24995,
        "usd": 1415.95,
        "is_primary": 0
      }
    ]
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
---
**6\.8 获取 Decentraland 地块成交均价统计信息接口**
###### 接口功能
> 获取 Decentraland 地块成交均价统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_avg_price_stats

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
        "mana": [
          {
            "time": "2022.01.30",
            "value_avg": 5494,
            "value_min": 4879,
            "value_max": 6150,
            "type": "land"
          },
          {
            "time": "2022.01.30",
            "value_avg": 27900,
            "value_min": 27900,
            "value_max": 27900,
            "type": "estate"
          },
          {
            "time": "2022.01.31",
            "value_avg": 6275,
            "value_min": 4998,
            "value_max": 11333,
            "type": "land"
          },
          {
            "time": "2022.01.31",
            "value_avg": 360000,
            "value_min": 360000,
            "value_max": 360000,
            "type": "estate"
          },
          {
            "time": "2022.02.01",
            "value_avg": 6836,
            "value_min": 4950,
            "value_max": 15888,
            "type": "land"
          },
          {
            "time": "2022.02.01",
            "value_avg": 48166,
            "value_min": 9000,
            "value_max": 69000,
            "type": "estate"
          },
          {
            "time": "2022.02.02",
            "value_avg": 5859,
            "value_min": 4939,
            "value_max": 6999,
            "type": "land"
          },
          {
            "time": "2022.02.02",
            "value_avg": 56944,
            "value_min": 48888,
            "value_max": 65000,
            "type": "estate"
          },
          {
            "time": "2022.02.03",
            "value_avg": 7183,
            "value_min": 5000,
            "value_max": 9999,
            "type": "land"
          },
          {
            "time": "2022.02.03",
            "value_avg": 29998,
            "value_min": 20000,
            "value_max": 39997,
            "type": "estate"
          },
          {
            "time": "2022.02.04",
            "value_avg": 6261,
            "value_min": 5100,
            "value_max": 12499,
            "type": "land"
          },
          {
            "time": "2022.02.04",
            "value_avg": 181999,
            "value_min": 11000,
            "value_max": 510000,
            "type": "estate"
          },
          {
            "time": "2022.02.05",
            "value_avg": 6292,
            "value_min": 5150,
            "value_max": 9999,
            "type": "land"
          },
          {
            "time": "2022.02.05",
            "value_avg": 29966,
            "value_min": 12000,
            "value_max": 45000,
            "type": "estate"
          },
          {
            "time": "2022.02.06",
            "value_avg": 6233,
            "value_min": 4799,
            "value_max": 8450,
            "type": "land"
          },
          {
            "time": "2022.02.06",
            "value_avg": 34573,
            "value_min": 21500,
            "value_max": 52221,
            "type": "estate"
          },
          {
            "time": "2022.02.07",
            "value_avg": 8001,
            "value_min": 4799,
            "value_max": 15650,
            "type": "land"
          },
          {
            "time": "2022.02.07",
            "value_avg": 36559,
            "value_min": 6997,
            "value_max": 69000,
            "type": "estate"
          },
          {
            "time": "2022.02.08",
            "value_avg": 5563,
            "value_min": 4600,
            "value_max": 8888,
            "type": "land"
          },
          {
            "time": "2022.02.08",
            "value_avg": 14499,
            "value_min": 9498,
            "value_max": 18000,
            "type": "estate"
          },
          {
            "time": "2022.02.09",
            "value_avg": 5931,
            "value_min": 4200,
            "value_max": 10419,
            "type": "land"
          },
          {
            "time": "2022.02.09",
            "value_avg": 17000,
            "value_min": 17000,
            "value_max": 17000,
            "type": "estate"
          },
          {
            "time": "2022.02.10",
            "value_avg": 6876,
            "value_min": 4697,
            "value_max": 10000,
            "type": "land"
          },
          {
            "time": "2022.02.10",
            "value_avg": 15500,
            "value_min": 15500,
            "value_max": 15500,
            "type": "estate"
          },
          {
            "time": "2022.02.11",
            "value_avg": 5386,
            "value_min": 4697,
            "value_max": 6456,
            "type": "land"
          },
          {
            "time": "2022.02.11",
            "value_avg": 10497,
            "value_min": 10497,
            "value_max": 10497,
            "type": "estate"
          },
          {
            "time": "2022.02.12",
            "value_avg": 6384,
            "value_min": 5245,
            "value_max": 10200,
            "type": "land"
          },
          {
            "time": "2022.02.12",
            "value_avg": 19420,
            "value_min": 19420,
            "value_max": 19420,
            "type": "estate"
          },
          {
            "time": "2022.02.13",
            "value_avg": 6648,
            "value_min": 5150,
            "value_max": 9250,
            "type": "land"
          },
          {
            "time": "2022.02.13",
            "value_avg": 45678,
            "value_min": 45678,
            "value_max": 45678,
            "type": "estate"
          },
          {
            "time": "2022.02.14",
            "value_avg": 6243,
            "value_min": 5169,
            "value_max": 7420,
            "type": "land"
          },
          {
            "time": "2022.02.14",
            "value_avg": 17890,
            "value_min": 17890,
            "value_max": 17890,
            "type": "estate"
          },
          {
            "time": "2022.02.15",
            "value_avg": 5986,
            "value_min": 4688,
            "value_max": 9000,
            "type": "land"
          },
          {
            "time": "2022.02.15",
            "value_avg": 20900,
            "value_min": 20900,
            "value_max": 20900,
            "type": "estate"
          },
          {
            "time": "2022.02.16",
            "value_avg": 7378,
            "value_min": 4950,
            "value_max": 11222,
            "type": "land"
          },
          {
            "time": "2022.02.16",
            "value_avg": 20140,
            "value_min": 17000,
            "value_max": 24000,
            "type": "estate"
          },
          {
            "time": "2022.02.17",
            "value_avg": 6540,
            "value_min": 4869,
            "value_max": 10000,
            "type": "land"
          },
          {
            "time": "2022.02.17",
            "value_avg": 14999,
            "value_min": 14999,
            "value_max": 14999,
            "type": "estate"
          },
          {
            "time": "2022.02.18",
            "value_avg": 7242,
            "value_min": 4400,
            "value_max": 15420,
            "type": "land"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.19",
            "value_avg": 5556,
            "value_min": 4600,
            "value_max": 6999,
            "type": "land"
          },
          {
            "time": "2022.02.19",
            "value_avg": 195500,
            "value_min": 76000,
            "value_max": 315000,
            "type": "estate"
          },
          {
            "time": "2022.02.20",
            "value_avg": 5886,
            "value_min": 4950,
            "value_max": 8800,
            "type": "land"
          },
          {
            "time": "2022.02.20",
            "value_avg": 23998,
            "value_min": 19997,
            "value_max": 28000,
            "type": "estate"
          },
          {
            "time": "2022.02.21",
            "value_avg": 6190,
            "value_min": 4032,
            "value_max": 9500,
            "type": "land"
          },
          {
            "time": "2022.02.21",
            "value_avg": 80000,
            "value_min": 80000,
            "value_max": 80000,
            "type": "estate"
          },
          {
            "time": "2022.02.22",
            "value_avg": 5877,
            "value_min": 4800,
            "value_max": 9000,
            "type": "land"
          },
          {
            "time": "2022.02.22",
            "value_avg": 9018,
            "value_min": 8049,
            "value_max": 9987,
            "type": "estate"
          },
          {
            "time": "2022.02.23",
            "value_avg": 7181,
            "value_min": 4300,
            "value_max": 15500,
            "type": "land"
          },
          {
            "time": "2022.02.23",
            "value_avg": 8314,
            "value_min": 8314,
            "value_max": 8314,
            "type": "estate"
          },
          {
            "time": "2022.02.24",
            "value_avg": 5418,
            "value_min": 4947,
            "value_max": 6888,
            "type": "land"
          },
          {
            "time": "2022.02.24",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.25",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.25",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.26",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.26",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.27",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.27",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.28",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.28",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          }
        ],
        "usd": [
          {
            "time": "2022.01.30",
            "value_avg": 13055,
            "value_min": 11594,
            "value_max": 14615,
            "type": "land"
          },
          {
            "time": "2022.01.30",
            "value_avg": 66300,
            "value_min": 66300,
            "value_max": 66300,
            "type": "estate"
          },
          {
            "time": "2022.01.31",
            "value_avg": 15878,
            "value_min": 12646,
            "value_max": 28675,
            "type": "land"
          },
          {
            "time": "2022.01.31",
            "value_avg": 910893,
            "value_min": 910893,
            "value_max": 910893,
            "type": "estate"
          },
          {
            "time": "2022.02.01",
            "value_avg": 19408,
            "value_min": 14052,
            "value_max": 45101,
            "type": "land"
          },
          {
            "time": "2022.02.01",
            "value_avg": 136731,
            "value_min": 25548,
            "value_max": 195871,
            "type": "estate"
          },
          {
            "time": "2022.02.02",
            "value_avg": 15804,
            "value_min": 13322,
            "value_max": 18879,
            "type": "land"
          },
          {
            "time": "2022.02.02",
            "value_avg": 153597,
            "value_min": 131867,
            "value_max": 175326,
            "type": "estate"
          },
          {
            "time": "2022.02.03",
            "value_avg": 18383,
            "value_min": 12796,
            "value_max": 25589,
            "type": "land"
          },
          {
            "time": "2022.02.03",
            "value_avg": 76771,
            "value_min": 51183,
            "value_max": 102359,
            "type": "estate"
          },
          {
            "time": "2022.02.04",
            "value_avg": 16655,
            "value_min": 13567,
            "value_max": 33249,
            "type": "land"
          },
          {
            "time": "2022.02.04",
            "value_avg": 484147,
            "value_min": 29261,
            "value_max": 1356683,
            "type": "estate"
          },
          {
            "time": "2022.02.05",
            "value_avg": 17795,
            "value_min": 14564,
            "value_max": 28276,
            "type": "land"
          },
          {
            "time": "2022.02.05",
            "value_avg": 84743,
            "value_min": 33935,
            "value_max": 127256,
            "type": "estate"
          },
          {
            "time": "2022.02.06",
            "value_avg": 18995,
            "value_min": 14624,
            "value_max": 25750,
            "type": "land"
          },
          {
            "time": "2022.02.06",
            "value_avg": 105356,
            "value_min": 65517,
            "value_max": 159133,
            "type": "estate"
          },
          {
            "time": "2022.02.07",
            "value_avg": 26555,
            "value_min": 15927,
            "value_max": 51938,
            "type": "land"
          },
          {
            "time": "2022.02.07",
            "value_avg": 121330,
            "value_min": 23221,
            "value_max": 228992,
            "type": "estate"
          },
          {
            "time": "2022.02.08",
            "value_avg": 18367,
            "value_min": 15187,
            "value_max": 29344,
            "type": "land"
          },
          {
            "time": "2022.02.08",
            "value_avg": 47870,
            "value_min": 31358,
            "value_max": 59428,
            "type": "estate"
          },
          {
            "time": "2022.02.09",
            "value_avg": 20734,
            "value_min": 14682,
            "value_max": 36421,
            "type": "land"
          },
          {
            "time": "2022.02.09",
            "value_avg": 59425,
            "value_min": 59425,
            "value_max": 59425,
            "type": "estate"
          },
          {
            "time": "2022.02.10",
            "value_avg": 23063,
            "value_min": 15754,
            "value_max": 33540,
            "type": "land"
          },
          {
            "time": "2022.02.10",
            "value_avg": 51986,
            "value_min": 51986,
            "value_max": 51986,
            "type": "estate"
          },
          {
            "time": "2022.02.11",
            "value_avg": 16991,
            "value_min": 14816,
            "value_max": 20364,
            "type": "land"
          },
          {
            "time": "2022.02.11",
            "value_avg": 33110,
            "value_min": 33110,
            "value_max": 33110,
            "type": "estate"
          },
          {
            "time": "2022.02.12",
            "value_avg": 18739,
            "value_min": 15394,
            "value_max": 29936,
            "type": "land"
          },
          {
            "time": "2022.02.12",
            "value_avg": 56996,
            "value_min": 56996,
            "value_max": 56996,
            "type": "estate"
          },
          {
            "time": "2022.02.13",
            "value_avg": 19378,
            "value_min": 15011,
            "value_max": 26962,
            "type": "land"
          },
          {
            "time": "2022.02.13",
            "value_avg": 133143,
            "value_min": 133143,
            "value_max": 133143,
            "type": "estate"
          },
          {
            "time": "2022.02.14",
            "value_avg": 17762,
            "value_min": 14706,
            "value_max": 21110,
            "type": "land"
          },
          {
            "time": "2022.02.14",
            "value_avg": 50897,
            "value_min": 50897,
            "value_max": 50897,
            "type": "estate"
          },
          {
            "time": "2022.02.15",
            "value_avg": 17073,
            "value_min": 13370,
            "value_max": 25668,
            "type": "land"
          },
          {
            "time": "2022.02.15",
            "value_avg": 59606,
            "value_min": 59606,
            "value_max": 59606,
            "type": "estate"
          },
          {
            "time": "2022.02.16",
            "value_avg": 24559,
            "value_min": 16476,
            "value_max": 37353,
            "type": "land"
          },
          {
            "time": "2022.02.16",
            "value_avg": 67036,
            "value_min": 56585,
            "value_max": 79884,
            "type": "estate"
          },
          {
            "time": "2022.02.17",
            "value_avg": 21459,
            "value_min": 15975,
            "value_max": 32810,
            "type": "land"
          },
          {
            "time": "2022.02.17",
            "value_avg": 49212,
            "value_min": 49212,
            "value_max": 49212,
            "type": "estate"
          },
          {
            "time": "2022.02.18",
            "value_avg": 22392,
            "value_min": 13605,
            "value_max": 47679,
            "type": "land"
          },
          {
            "time": "2022.02.18",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.19",
            "value_avg": 16611,
            "value_min": 13752,
            "value_max": 20924,
            "type": "land"
          },
          {
            "time": "2022.02.19",
            "value_avg": 584460,
            "value_min": 227207,
            "value_max": 941714,
            "type": "estate"
          },
          {
            "time": "2022.02.20",
            "value_avg": 17133,
            "value_min": 14407,
            "value_max": 25613,
            "type": "land"
          },
          {
            "time": "2022.02.20",
            "value_avg": 69847,
            "value_min": 58201,
            "value_max": 81494,
            "type": "estate"
          },
          {
            "time": "2022.02.21",
            "value_avg": 16790,
            "value_min": 10935,
            "value_max": 25765,
            "type": "land"
          },
          {
            "time": "2022.02.21",
            "value_avg": 216972,
            "value_min": 216972,
            "value_max": 216972,
            "type": "estate"
          },
          {
            "time": "2022.02.22",
            "value_avg": 14656,
            "value_min": 11969,
            "value_max": 22442,
            "type": "land"
          },
          {
            "time": "2022.02.22",
            "value_avg": 22486,
            "value_min": 20070,
            "value_max": 24902,
            "type": "estate"
          },
          {
            "time": "2022.02.23",
            "value_avg": 19004,
            "value_min": 11380,
            "value_max": 41019,
            "type": "land"
          },
          {
            "time": "2022.02.23",
            "value_avg": 22002,
            "value_min": 22002,
            "value_max": 22002,
            "type": "estate"
          },
          {
            "time": "2022.02.24",
            "value_avg": 14006,
            "value_min": 12789,
            "value_max": 17807,
            "type": "land"
          },
          {
            "time": "2022.02.24",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.25",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.25",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.26",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.26",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.27",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.27",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          },
          {
            "time": "2022.02.28",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "land"
          },
          {
            "time": "2022.02.28",
            "value_avg": 0,
            "value_min": 0,
            "value_max": 0,
            "type": "estate"
          }
        ]
      }
    },
    "monthly": {
      "data": {
        "mana": [
          {
            "time": "2019.09",
            "value_avg": 18793,
            "value_min": 9000,
            "value_max": 210000,
            "type": "land"
          },
          {
            "time": "2019.09",
            "value_avg": 149135,
            "value_min": 23500,
            "value_max": 1150000,
            "type": "estate"
          },
          {
            "time": "2019.10",
            "value_avg": 18837,
            "value_min": 8000,
            "value_max": 60000,
            "type": "land"
          },
          {
            "time": "2019.10",
            "value_avg": 56225,
            "value_min": 23998,
            "value_max": 138000,
            "type": "estate"
          },
          {
            "time": "2019.11",
            "value_avg": 20056,
            "value_min": 5000,
            "value_max": 225000,
            "type": "land"
          },
          {
            "time": "2019.11",
            "value_avg": 215874,
            "value_min": 38000,
            "value_max": 425000,
            "type": "estate"
          },
          {
            "time": "2019.12",
            "value_avg": 17597,
            "value_min": 8000,
            "value_max": 150000,
            "type": "land"
          },
          {
            "time": "2019.12",
            "value_avg": 196360,
            "value_min": 55555,
            "value_max": 530000,
            "type": "estate"
          },
          {
            "time": "2020.01",
            "value_avg": 21197,
            "value_min": 1,
            "value_max": 128000,
            "type": "land"
          },
          {
            "time": "2020.01",
            "value_avg": 91088,
            "value_min": 27000,
            "value_max": 212000,
            "type": "estate"
          },
          {
            "time": "2020.02",
            "value_avg": 22628,
            "value_min": 100,
            "value_max": 149000,
            "type": "land"
          },
          {
            "time": "2020.02",
            "value_avg": 125022,
            "value_min": 1,
            "value_max": 750000,
            "type": "estate"
          },
          {
            "time": "2020.03",
            "value_avg": 18217,
            "value_min": 10000,
            "value_max": 79600,
            "type": "land"
          },
          {
            "time": "2020.03",
            "value_avg": 113811,
            "value_min": 28000,
            "value_max": 999989,
            "type": "estate"
          },
          {
            "time": "2020.04",
            "value_avg": 20080,
            "value_min": 2345,
            "value_max": 99000,
            "type": "land"
          },
          {
            "time": "2020.04",
            "value_avg": 156990,
            "value_min": 24000,
            "value_max": 1370000,
            "type": "estate"
          },
          {
            "time": "2020.05",
            "value_avg": 18724,
            "value_min": 1999,
            "value_max": 85000,
            "type": "land"
          },
          {
            "time": "2020.05",
            "value_avg": 188817,
            "value_min": 27500,
            "value_max": 1400000,
            "type": "estate"
          },
          {
            "time": "2020.06",
            "value_avg": 20038,
            "value_min": 9000,
            "value_max": 85000,
            "type": "land"
          },
          {
            "time": "2020.06",
            "value_avg": 145614,
            "value_min": 26800,
            "value_max": 595000,
            "type": "estate"
          },
          {
            "time": "2020.07",
            "value_avg": 18687,
            "value_min": 10000,
            "value_max": 77000,
            "type": "land"
          },
          {
            "time": "2020.07",
            "value_avg": 55264,
            "value_min": 30000,
            "value_max": 150000,
            "type": "estate"
          },
          {
            "time": "2020.08",
            "value_avg": 15079,
            "value_min": 6380,
            "value_max": 90000,
            "type": "land"
          },
          {
            "time": "2020.08",
            "value_avg": 59555,
            "value_min": 20999,
            "value_max": 300000,
            "type": "estate"
          },
          {
            "time": "2020.09",
            "value_avg": 13136,
            "value_min": 8000,
            "value_max": 41999,
            "type": "land"
          },
          {
            "time": "2020.09",
            "value_avg": 69061,
            "value_min": 19800,
            "value_max": 199999,
            "type": "estate"
          },
          {
            "time": "2020.10",
            "value_avg": 12443,
            "value_min": 1,
            "value_max": 32000,
            "type": "land"
          },
          {
            "time": "2020.10",
            "value_avg": 60955,
            "value_min": 16000,
            "value_max": 225000,
            "type": "estate"
          },
          {
            "time": "2020.11",
            "value_avg": 13156,
            "value_min": 5500,
            "value_max": 59500,
            "type": "land"
          },
          {
            "time": "2020.11",
            "value_avg": 58027,
            "value_min": 14999,
            "value_max": 360000,
            "type": "estate"
          },
          {
            "time": "2020.12",
            "value_avg": 10686,
            "value_min": 6000,
            "value_max": 64000,
            "type": "land"
          },
          {
            "time": "2020.12",
            "value_avg": 46206,
            "value_min": 15990,
            "value_max": 225000,
            "type": "estate"
          },
          {
            "time": "2021.01",
            "value_avg": 12506,
            "value_min": 6200,
            "value_max": 78888,
            "type": "land"
          },
          {
            "time": "2021.01",
            "value_avg": 76643,
            "value_min": 12000,
            "value_max": 500000,
            "type": "estate"
          },
          {
            "time": "2021.02",
            "value_avg": 12017,
            "value_min": 4000,
            "value_max": 180000,
            "type": "land"
          },
          {
            "time": "2021.02",
            "value_avg": 76315,
            "value_min": 12499,
            "value_max": 411000,
            "type": "estate"
          },
          {
            "time": "2021.03",
            "value_avg": 9374,
            "value_min": 2600,
            "value_max": 69420,
            "type": "land"
          },
          {
            "time": "2021.03",
            "value_avg": 56162,
            "value_min": 1300,
            "value_max": 300000,
            "type": "estate"
          },
          {
            "time": "2021.04",
            "value_avg": 7262,
            "value_min": 3988,
            "value_max": 30000,
            "type": "land"
          },
          {
            "time": "2021.04",
            "value_avg": 53849,
            "value_min": 10000,
            "value_max": 301000,
            "type": "estate"
          },
          {
            "time": "2021.05",
            "value_avg": 5813,
            "value_min": 3699,
            "value_max": 14700,
            "type": "land"
          },
          {
            "time": "2021.05",
            "value_avg": 40666,
            "value_min": 7000,
            "value_max": 759361,
            "type": "estate"
          },
          {
            "time": "2021.06",
            "value_avg": 6620,
            "value_min": 3332,
            "value_max": 47887,
            "type": "land"
          },
          {
            "time": "2021.06",
            "value_avg": 57298,
            "value_min": 8888,
            "value_max": 1295000,
            "type": "estate"
          },
          {
            "time": "2021.07",
            "value_avg": 7004,
            "value_min": 4100,
            "value_max": 16900,
            "type": "land"
          },
          {
            "time": "2021.07",
            "value_avg": 24948,
            "value_min": 8500,
            "value_max": 98000,
            "type": "estate"
          },
          {
            "time": "2021.08",
            "value_avg": 6632,
            "value_min": 4420,
            "value_max": 15000,
            "type": "land"
          },
          {
            "time": "2021.08",
            "value_avg": 28921,
            "value_min": 8000,
            "value_max": 158000,
            "type": "estate"
          },
          {
            "time": "2021.09",
            "value_avg": 6879,
            "value_min": 500,
            "value_max": 49999,
            "type": "land"
          },
          {
            "time": "2021.09",
            "value_avg": 36337,
            "value_min": 10000,
            "value_max": 250000,
            "type": "estate"
          },
          {
            "time": "2021.10",
            "value_avg": 7459,
            "value_min": 3000,
            "value_max": 52000,
            "type": "land"
          },
          {
            "time": "2021.10",
            "value_avg": 38641,
            "value_min": 20,
            "value_max": 350000,
            "type": "estate"
          },
          {
            "time": "2021.11",
            "value_avg": 4955,
            "value_min": 700,
            "value_max": 28000,
            "type": "land"
          },
          {
            "time": "2021.11",
            "value_avg": 42819,
            "value_min": 5000,
            "value_max": 618000,
            "type": "estate"
          },
          {
            "time": "2021.12",
            "value_avg": 5468,
            "value_min": 3,
            "value_max": 125000,
            "type": "land"
          },
          {
            "time": "2021.12",
            "value_avg": 45556,
            "value_min": 6000,
            "value_max": 300000,
            "type": "estate"
          },
          {
            "time": "2022.01",
            "value_avg": 6041,
            "value_min": 1490,
            "value_max": 24999,
            "type": "land"
          },
          {
            "time": "2022.01",
            "value_avg": 53284,
            "value_min": 10,
            "value_max": 425000,
            "type": "estate"
          },
          {
            "time": "2022.02",
            "value_avg": 6328,
            "value_min": 4032,
            "value_max": 15888,
            "type": "land"
          },
          {
            "time": "2022.02",
            "value_avg": 47719,
            "value_min": 6997,
            "value_max": 510000,
            "type": "estate"
          }
        ],
        "usd": [
          {
            "time": "2019.09",
            "value_avg": 597,
            "value_min": 271,
            "value_max": 5958,
            "type": "land"
          },
          {
            "time": "2019.09",
            "value_avg": 4757,
            "value_min": 763,
            "value_max": 37351,
            "type": "estate"
          },
          {
            "time": "2019.10",
            "value_avg": 578,
            "value_min": 245,
            "value_max": 1910,
            "type": "land"
          },
          {
            "time": "2019.10",
            "value_avg": 1767,
            "value_min": 667,
            "value_max": 4425,
            "type": "estate"
          },
          {
            "time": "2019.11",
            "value_avg": 565,
            "value_min": 149,
            "value_max": 6429,
            "type": "land"
          },
          {
            "time": "2019.11",
            "value_avg": 5610,
            "value_min": 1205,
            "value_max": 12631,
            "type": "estate"
          },
          {
            "time": "2019.12",
            "value_avg": 483,
            "value_min": 203,
            "value_max": 3781,
            "type": "land"
          },
          {
            "time": "2019.12",
            "value_avg": 5322,
            "value_min": 1454,
            "value_max": 14069,
            "type": "estate"
          },
          {
            "time": "2020.01",
            "value_avg": 742,
            "value_min": 0,
            "value_max": 4551,
            "type": "land"
          },
          {
            "time": "2020.01",
            "value_avg": 3133,
            "value_min": 956,
            "value_max": 7189,
            "type": "estate"
          },
          {
            "time": "2020.02",
            "value_avg": 1255,
            "value_min": 6,
            "value_max": 9730,
            "type": "land"
          },
          {
            "time": "2020.02",
            "value_avg": 7236,
            "value_min": 0,
            "value_max": 48068,
            "type": "estate"
          },
          {
            "time": "2020.03",
            "value_avg": 547,
            "value_min": 210,
            "value_max": 2718,
            "type": "land"
          },
          {
            "time": "2020.03",
            "value_avg": 2715,
            "value_min": 685,
            "value_max": 22143,
            "type": "estate"
          },
          {
            "time": "2020.04",
            "value_avg": 564,
            "value_min": 71,
            "value_max": 2836,
            "type": "land"
          },
          {
            "time": "2020.04",
            "value_avg": 4608,
            "value_min": 772,
            "value_max": 40137,
            "type": "estate"
          },
          {
            "time": "2020.05",
            "value_avg": 685,
            "value_min": 81,
            "value_max": 3347,
            "type": "land"
          },
          {
            "time": "2020.05",
            "value_avg": 6990,
            "value_min": 992,
            "value_max": 54345,
            "type": "estate"
          },
          {
            "time": "2020.06",
            "value_avg": 820,
            "value_min": 395,
            "value_max": 3404,
            "type": "land"
          },
          {
            "time": "2020.06",
            "value_avg": 5997,
            "value_min": 1129,
            "value_max": 24142,
            "type": "estate"
          },
          {
            "time": "2020.07",
            "value_avg": 753,
            "value_min": 465,
            "value_max": 3062,
            "type": "land"
          },
          {
            "time": "2020.07",
            "value_avg": 2302,
            "value_min": 1210,
            "value_max": 6391,
            "type": "estate"
          },
          {
            "time": "2020.08",
            "value_avg": 1303,
            "value_min": 508,
            "value_max": 4890,
            "type": "land"
          },
          {
            "time": "2020.08",
            "value_avg": 5356,
            "value_min": 1615,
            "value_max": 31077,
            "type": "estate"
          },
          {
            "time": "2020.09",
            "value_avg": 1034,
            "value_min": 606,
            "value_max": 3437,
            "type": "land"
          },
          {
            "time": "2020.09",
            "value_avg": 5551,
            "value_min": 1356,
            "value_max": 16171,
            "type": "estate"
          },
          {
            "time": "2020.10",
            "value_avg": 923,
            "value_min": 0,
            "value_max": 2271,
            "type": "land"
          },
          {
            "time": "2020.10",
            "value_avg": 4519,
            "value_min": 1183,
            "value_max": 16853,
            "type": "estate"
          },
          {
            "time": "2020.11",
            "value_avg": 1071,
            "value_min": 448,
            "value_max": 4404,
            "type": "land"
          },
          {
            "time": "2020.11",
            "value_avg": 4634,
            "value_min": 976,
            "value_max": 29755,
            "type": "estate"
          },
          {
            "time": "2020.12",
            "value_avg": 904,
            "value_min": 500,
            "value_max": 5069,
            "type": "land"
          },
          {
            "time": "2020.12",
            "value_avg": 3870,
            "value_min": 1346,
            "value_max": 18219,
            "type": "estate"
          },
          {
            "time": "2021.01",
            "value_avg": 1575,
            "value_min": 572,
            "value_max": 10895,
            "type": "land"
          },
          {
            "time": "2021.01",
            "value_avg": 10814,
            "value_min": 1504,
            "value_max": 77803,
            "type": "estate"
          },
          {
            "time": "2021.02",
            "value_avg": 3084,
            "value_min": 944,
            "value_max": 53525,
            "type": "land"
          },
          {
            "time": "2021.02",
            "value_avg": 18854,
            "value_min": 3004,
            "value_max": 104741,
            "type": "estate"
          },
          {
            "time": "2021.03",
            "value_avg": 6585,
            "value_min": 1184,
            "value_max": 66279,
            "type": "land"
          },
          {
            "time": "2021.03",
            "value_avg": 41815,
            "value_min": 638,
            "value_max": 294837,
            "type": "estate"
          },
          {
            "time": "2021.04",
            "value_avg": 8380,
            "value_min": 4063,
            "value_max": 32721,
            "type": "land"
          },
          {
            "time": "2021.04",
            "value_avg": 63765,
            "value_min": 9426,
            "value_max": 403665,
            "type": "estate"
          },
          {
            "time": "2021.05",
            "value_avg": 6707,
            "value_min": 2505,
            "value_max": 18306,
            "type": "land"
          },
          {
            "time": "2021.05",
            "value_avg": 42343,
            "value_min": 5636,
            "value_max": 758891,
            "type": "estate"
          },
          {
            "time": "2021.06",
            "value_avg": 4340,
            "value_min": 2093,
            "value_max": 34201,
            "type": "land"
          },
          {
            "time": "2021.06",
            "value_avg": 38116,
            "value_min": 3934,
            "value_max": 896747,
            "type": "estate"
          },
          {
            "time": "2021.07",
            "value_avg": 4396,
            "value_min": 2609,
            "value_max": 9942,
            "type": "land"
          },
          {
            "time": "2021.07",
            "value_avg": 15330,
            "value_min": 4943,
            "value_max": 56850,
            "type": "estate"
          },
          {
            "time": "2021.08",
            "value_avg": 5517,
            "value_min": 3225,
            "value_max": 13534,
            "type": "land"
          },
          {
            "time": "2021.08",
            "value_avg": 22978,
            "value_min": 5832,
            "value_max": 134475,
            "type": "estate"
          },
          {
            "time": "2021.09",
            "value_avg": 6047,
            "value_min": 537,
            "value_max": 41372,
            "type": "land"
          },
          {
            "time": "2021.09",
            "value_avg": 27997,
            "value_min": 6116,
            "value_max": 188574,
            "type": "estate"
          },
          {
            "time": "2021.10",
            "value_avg": 8353,
            "value_min": 3448,
            "value_max": 39903,
            "type": "land"
          },
          {
            "time": "2021.10",
            "value_avg": 36052,
            "value_min": 70,
            "value_max": 274668,
            "type": "estate"
          },
          {
            "time": "2021.11",
            "value_avg": 18703,
            "value_min": 2279,
            "value_max": 102329,
            "type": "land"
          },
          {
            "time": "2021.11",
            "value_avg": 175810,
            "value_min": 22760,
            "value_max": 2514870,
            "type": "estate"
          },
          {
            "time": "2021.12",
            "value_avg": 19827,
            "value_min": 10,
            "value_max": 434811,
            "type": "land"
          },
          {
            "time": "2021.12",
            "value_avg": 167103,
            "value_min": 19785,
            "value_max": 1043547,
            "type": "estate"
          },
          {
            "time": "2022.01",
            "value_avg": 16573,
            "value_min": 4589,
            "value_max": 83779,
            "type": "land"
          },
          {
            "time": "2022.01",
            "value_avg": 146983,
            "value_min": 32,
            "value_max": 1166084,
            "type": "estate"
          },
          {
            "time": "2022.02",
            "value_avg": 18630,
            "value_min": 10935,
            "value_max": 51938,
            "type": "land"
          },
          {
            "time": "2022.02",
            "value_avg": 137953,
            "value_min": 20070,
            "value_max": 1356683,
            "type": "estate"
          }
        ]
      }
    }
  }
}
```
---
**6\.9 获取 Decentraland 地块成交总数量统计信息接口**
###### 接口功能
> 获取 Decentraland 地块成交总数量统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_sold_total_stats

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
          "time": "2022.01.30",
          "value": 9,
          "type": "land"
        },
        {
          "time": "2022.01.30",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.01.31",
          "value": 13,
          "type": "land"
        },
        {
          "time": "2022.01.31",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.01",
          "value": 13,
          "type": "land"
        },
        {
          "time": "2022.02.01",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.02",
          "value": 17,
          "type": "land"
        },
        {
          "time": "2022.02.02",
          "value": 2,
          "type": "estate"
        },
        {
          "time": "2022.02.03",
          "value": 13,
          "type": "land"
        },
        {
          "time": "2022.02.03",
          "value": 2,
          "type": "estate"
        },
        {
          "time": "2022.02.04",
          "value": 10,
          "type": "land"
        },
        {
          "time": "2022.02.04",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.05",
          "value": 12,
          "type": "land"
        },
        {
          "time": "2022.02.05",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.06",
          "value": 13,
          "type": "land"
        },
        {
          "time": "2022.02.06",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.07",
          "value": 9,
          "type": "land"
        },
        {
          "time": "2022.02.07",
          "value": 5,
          "type": "estate"
        },
        {
          "time": "2022.02.08",
          "value": 10,
          "type": "land"
        },
        {
          "time": "2022.02.08",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.09",
          "value": 19,
          "type": "land"
        },
        {
          "time": "2022.02.09",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.10",
          "value": 8,
          "type": "land"
        },
        {
          "time": "2022.02.10",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.11",
          "value": 7,
          "type": "land"
        },
        {
          "time": "2022.02.11",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.12",
          "value": 9,
          "type": "land"
        },
        {
          "time": "2022.02.12",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.13",
          "value": 8,
          "type": "land"
        },
        {
          "time": "2022.02.13",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.14",
          "value": 5,
          "type": "land"
        },
        {
          "time": "2022.02.14",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.15",
          "value": 6,
          "type": "land"
        },
        {
          "time": "2022.02.15",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.16",
          "value": 8,
          "type": "land"
        },
        {
          "time": "2022.02.16",
          "value": 3,
          "type": "estate"
        },
        {
          "time": "2022.02.17",
          "value": 8,
          "type": "land"
        },
        {
          "time": "2022.02.17",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.18",
          "value": 5,
          "type": "land"
        },
        {
          "time": "2022.02.18",
          "value": 0,
          "type": "estate"
        },
        {
          "time": "2022.02.19",
          "value": 11,
          "type": "land"
        },
        {
          "time": "2022.02.19",
          "value": 2,
          "type": "estate"
        },
        {
          "time": "2022.02.20",
          "value": 14,
          "type": "land"
        },
        {
          "time": "2022.02.20",
          "value": 2,
          "type": "estate"
        },
        {
          "time": "2022.02.21",
          "value": 11,
          "type": "land"
        },
        {
          "time": "2022.02.21",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.22",
          "value": 12,
          "type": "land"
        },
        {
          "time": "2022.02.22",
          "value": 2,
          "type": "estate"
        },
        {
          "time": "2022.02.23",
          "value": 11,
          "type": "land"
        },
        {
          "time": "2022.02.23",
          "value": 1,
          "type": "estate"
        },
        {
          "time": "2022.02.24",
          "value": 9,
          "type": "land"
        },
        {
          "time": "2022.02.24",
          "value": 0,
          "type": "estate"
        },
        {
          "time": "2022.02.25",
          "value": 0,
          "type": "land"
        },
        {
          "time": "2022.02.25",
          "value": 0,
          "type": "estate"
        },
        {
          "time": "2022.02.26",
          "value": 0,
          "type": "land"
        },
        {
          "time": "2022.02.26",
          "value": 0,
          "type": "estate"
        },
        {
          "time": "2022.02.27",
          "value": 0,
          "type": "land"
        },
        {
          "time": "2022.02.27",
          "value": 0,
          "type": "estate"
        },
        {
          "time": "2022.02.28",
          "value": 0,
          "type": "land"
        },
        {
          "time": "2022.02.28",
          "value": 0,
          "type": "estate"
        }
      ]
    },
    "monthly": {
      "data": [
        {
          "time": "2019.09",
          "value": 123,
          "type": "land"
        },
        {
          "time": "2019.09",
          "value": 18,
          "type": "estate"
        },
        {
          "time": "2019.10",
          "value": 172,
          "type": "land"
        },
        {
          "time": "2019.10",
          "value": 16,
          "type": "estate"
        },
        {
          "time": "2019.11",
          "value": 103,
          "type": "land"
        },
        {
          "time": "2019.11",
          "value": 8,
          "type": "estate"
        },
        {
          "time": "2019.12",
          "value": 147,
          "type": "land"
        },
        {
          "time": "2019.12",
          "value": 14,
          "type": "estate"
        },
        {
          "time": "2020.01",
          "value": 236,
          "type": "land"
        },
        {
          "time": "2020.01",
          "value": 22,
          "type": "estate"
        },
        {
          "time": "2020.02",
          "value": 538,
          "type": "land"
        },
        {
          "time": "2020.02",
          "value": 62,
          "type": "estate"
        },
        {
          "time": "2020.03",
          "value": 175,
          "type": "land"
        },
        {
          "time": "2020.03",
          "value": 27,
          "type": "estate"
        },
        {
          "time": "2020.04",
          "value": 128,
          "type": "land"
        },
        {
          "time": "2020.04",
          "value": 39,
          "type": "estate"
        },
        {
          "time": "2020.05",
          "value": 138,
          "type": "land"
        },
        {
          "time": "2020.05",
          "value": 22,
          "type": "estate"
        },
        {
          "time": "2020.06",
          "value": 86,
          "type": "land"
        },
        {
          "time": "2020.06",
          "value": 26,
          "type": "estate"
        },
        {
          "time": "2020.07",
          "value": 131,
          "type": "land"
        },
        {
          "time": "2020.07",
          "value": 20,
          "type": "estate"
        },
        {
          "time": "2020.08",
          "value": 146,
          "type": "land"
        },
        {
          "time": "2020.08",
          "value": 14,
          "type": "estate"
        },
        {
          "time": "2020.09",
          "value": 128,
          "type": "land"
        },
        {
          "time": "2020.09",
          "value": 19,
          "type": "estate"
        },
        {
          "time": "2020.10",
          "value": 135,
          "type": "land"
        },
        {
          "time": "2020.10",
          "value": 26,
          "type": "estate"
        },
        {
          "time": "2020.11",
          "value": 103,
          "type": "land"
        },
        {
          "time": "2020.11",
          "value": 25,
          "type": "estate"
        },
        {
          "time": "2020.12",
          "value": 169,
          "type": "land"
        },
        {
          "time": "2020.12",
          "value": 35,
          "type": "estate"
        },
        {
          "time": "2021.01",
          "value": 156,
          "type": "land"
        },
        {
          "time": "2021.01",
          "value": 59,
          "type": "estate"
        },
        {
          "time": "2021.02",
          "value": 230,
          "type": "land"
        },
        {
          "time": "2021.02",
          "value": 30,
          "type": "estate"
        },
        {
          "time": "2021.03",
          "value": 536,
          "type": "land"
        },
        {
          "time": "2021.03",
          "value": 58,
          "type": "estate"
        },
        {
          "time": "2021.04",
          "value": 297,
          "type": "land"
        },
        {
          "time": "2021.04",
          "value": 61,
          "type": "estate"
        },
        {
          "time": "2021.05",
          "value": 214,
          "type": "land"
        },
        {
          "time": "2021.05",
          "value": 39,
          "type": "estate"
        },
        {
          "time": "2021.06",
          "value": 162,
          "type": "land"
        },
        {
          "time": "2021.06",
          "value": 50,
          "type": "estate"
        },
        {
          "time": "2021.07",
          "value": 121,
          "type": "land"
        },
        {
          "time": "2021.07",
          "value": 34,
          "type": "estate"
        },
        {
          "time": "2021.08",
          "value": 144,
          "type": "land"
        },
        {
          "time": "2021.08",
          "value": 57,
          "type": "estate"
        },
        {
          "time": "2021.09",
          "value": 283,
          "type": "land"
        },
        {
          "time": "2021.09",
          "value": 53,
          "type": "estate"
        },
        {
          "time": "2021.10",
          "value": 250,
          "type": "land"
        },
        {
          "time": "2021.10",
          "value": 66,
          "type": "estate"
        },
        {
          "time": "2021.11",
          "value": 565,
          "type": "land"
        },
        {
          "time": "2021.11",
          "value": 65,
          "type": "estate"
        },
        {
          "time": "2021.12",
          "value": 679,
          "type": "land"
        },
        {
          "time": "2021.12",
          "value": 69,
          "type": "estate"
        },
        {
          "time": "2022.01",
          "value": 488,
          "type": "land"
        },
        {
          "time": "2022.01",
          "value": 60,
          "type": "estate"
        },
        {
          "time": "2022.02",
          "value": 248,
          "type": "land"
        },
        {
          "time": "2022.02",
          "value": 43,
          "type": "estate"
        }
      ]
    }
  }
}
```
---
**6\.10 获取 Decentraland 地块销售总额统计信息接口**
###### 接口功能
> 获取 Decentraland 地块销售总额统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_sold_sum_stats

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
    "mana": {
      "data": [
        {
          "time": "2019.09",
          "value": 2311616,
          "type": "land"
        },
        {
          "time": "2019.09",
          "value": 2684442,
          "type": "estate"
        },
        {
          "time": "2019.10",
          "value": 3240082,
          "type": "land"
        },
        {
          "time": "2019.10",
          "value": 899606,
          "type": "estate"
        },
        {
          "time": "2019.11",
          "value": 2065864,
          "type": "land"
        },
        {
          "time": "2019.11",
          "value": 1726999,
          "type": "estate"
        },
        {
          "time": "2019.12",
          "value": 2586766,
          "type": "land"
        },
        {
          "time": "2019.12",
          "value": 2749047,
          "type": "estate"
        },
        {
          "time": "2020.01",
          "value": 5002692,
          "type": "land"
        },
        {
          "time": "2020.01",
          "value": 2003949,
          "type": "estate"
        },
        {
          "time": "2020.02",
          "value": 12173892,
          "type": "land"
        },
        {
          "time": "2020.02",
          "value": 7751371,
          "type": "estate"
        },
        {
          "time": "2020.03",
          "value": 3188049,
          "type": "land"
        },
        {
          "time": "2020.03",
          "value": 3072916,
          "type": "estate"
        },
        {
          "time": "2020.04",
          "value": 2570276,
          "type": "land"
        },
        {
          "time": "2020.04",
          "value": 6122614,
          "type": "estate"
        },
        {
          "time": "2020.05",
          "value": 2583942,
          "type": "land"
        },
        {
          "time": "2020.05",
          "value": 4153994,
          "type": "estate"
        },
        {
          "time": "2020.06",
          "value": 1723348,
          "type": "land"
        },
        {
          "time": "2020.06",
          "value": 3785973,
          "type": "estate"
        },
        {
          "time": "2020.07",
          "value": 2448024,
          "type": "land"
        },
        {
          "time": "2020.07",
          "value": 1105298,
          "type": "estate"
        },
        {
          "time": "2020.08",
          "value": 2201670,
          "type": "land"
        },
        {
          "time": "2020.08",
          "value": 833782,
          "type": "estate"
        },
        {
          "time": "2020.09",
          "value": 1681478,
          "type": "land"
        },
        {
          "time": "2020.09",
          "value": 1312173,
          "type": "estate"
        },
        {
          "time": "2020.10",
          "value": 1679925,
          "type": "land"
        },
        {
          "time": "2020.10",
          "value": 1584835,
          "type": "estate"
        },
        {
          "time": "2020.11",
          "value": 1355139,
          "type": "land"
        },
        {
          "time": "2020.11",
          "value": 1450693,
          "type": "estate"
        },
        {
          "time": "2020.12",
          "value": 1806027,
          "type": "land"
        },
        {
          "time": "2020.12",
          "value": 1617243,
          "type": "estate"
        },
        {
          "time": "2021.01",
          "value": 1950936,
          "type": "land"
        },
        {
          "time": "2021.01",
          "value": 4521962,
          "type": "estate"
        },
        {
          "time": "2021.02",
          "value": 2764083,
          "type": "land"
        },
        {
          "time": "2021.02",
          "value": 2289452,
          "type": "estate"
        },
        {
          "time": "2021.03",
          "value": 5024514,
          "type": "land"
        },
        {
          "time": "2021.03",
          "value": 3257407,
          "type": "estate"
        },
        {
          "time": "2021.04",
          "value": 2156824,
          "type": "land"
        },
        {
          "time": "2021.04",
          "value": 3284795,
          "type": "estate"
        },
        {
          "time": "2021.05",
          "value": 1244016,
          "type": "land"
        },
        {
          "time": "2021.05",
          "value": 1586006,
          "type": "estate"
        },
        {
          "time": "2021.06",
          "value": 1072529,
          "type": "land"
        },
        {
          "time": "2021.06",
          "value": 2864900,
          "type": "estate"
        },
        {
          "time": "2021.07",
          "value": 847536,
          "type": "land"
        },
        {
          "time": "2021.07",
          "value": 848234,
          "type": "estate"
        },
        {
          "time": "2021.08",
          "value": 955009,
          "type": "land"
        },
        {
          "time": "2021.08",
          "value": 1648503,
          "type": "estate"
        },
        {
          "time": "2021.09",
          "value": 1947016,
          "type": "land"
        },
        {
          "time": "2021.09",
          "value": 1925905,
          "type": "estate"
        },
        {
          "time": "2021.10",
          "value": 1864754,
          "type": "land"
        },
        {
          "time": "2021.10",
          "value": 2550334,
          "type": "estate"
        },
        {
          "time": "2021.11",
          "value": 2799690,
          "type": "land"
        },
        {
          "time": "2021.11",
          "value": 2783275,
          "type": "estate"
        },
        {
          "time": "2021.12",
          "value": 3713373,
          "type": "land"
        },
        {
          "time": "2021.12",
          "value": 3143376,
          "type": "estate"
        },
        {
          "time": "2022.01",
          "value": 2948337,
          "type": "land"
        },
        {
          "time": "2022.01",
          "value": 3197083,
          "type": "estate"
        },
        {
          "time": "2022.02",
          "value": 1569370,
          "type": "land"
        },
        {
          "time": "2022.02",
          "value": 2051949,
          "type": "estate"
        }
      ]
    },
    "usd": {
      "data": [
        {
          "time": "2019.09",
          "value": 73517,
          "type": "land"
        },
        {
          "time": "2019.09",
          "value": 85643,
          "type": "estate"
        },
        {
          "time": "2019.10",
          "value": 99440,
          "type": "land"
        },
        {
          "time": "2019.10",
          "value": 28283,
          "type": "estate"
        },
        {
          "time": "2019.11",
          "value": 58289,
          "type": "land"
        },
        {
          "time": "2019.11",
          "value": 44885,
          "type": "estate"
        },
        {
          "time": "2019.12",
          "value": 71056,
          "type": "land"
        },
        {
          "time": "2019.12",
          "value": 74508,
          "type": "estate"
        },
        {
          "time": "2020.01",
          "value": 175148,
          "type": "land"
        },
        {
          "time": "2020.01",
          "value": 68927,
          "type": "estate"
        },
        {
          "time": "2020.02",
          "value": 675282,
          "type": "land"
        },
        {
          "time": "2020.02",
          "value": 448640,
          "type": "estate"
        },
        {
          "time": "2020.03",
          "value": 95797,
          "type": "land"
        },
        {
          "time": "2020.03",
          "value": 73323,
          "type": "estate"
        },
        {
          "time": "2020.04",
          "value": 72216,
          "type": "land"
        },
        {
          "time": "2020.04",
          "value": 179731,
          "type": "estate"
        },
        {
          "time": "2020.05",
          "value": 94535,
          "type": "land"
        },
        {
          "time": "2020.05",
          "value": 153796,
          "type": "estate"
        },
        {
          "time": "2020.06",
          "value": 70568,
          "type": "land"
        },
        {
          "time": "2020.06",
          "value": 155924,
          "type": "estate"
        },
        {
          "time": "2020.07",
          "value": 98718,
          "type": "land"
        },
        {
          "time": "2020.07",
          "value": 46041,
          "type": "estate"
        },
        {
          "time": "2020.08",
          "value": 190305,
          "type": "land"
        },
        {
          "time": "2020.08",
          "value": 74988,
          "type": "estate"
        },
        {
          "time": "2020.09",
          "value": 132368,
          "type": "land"
        },
        {
          "time": "2020.09",
          "value": 105471,
          "type": "estate"
        },
        {
          "time": "2020.10",
          "value": 124635,
          "type": "land"
        },
        {
          "time": "2020.10",
          "value": 117511,
          "type": "estate"
        },
        {
          "time": "2020.11",
          "value": 110363,
          "type": "land"
        },
        {
          "time": "2020.11",
          "value": 115854,
          "type": "estate"
        },
        {
          "time": "2020.12",
          "value": 152817,
          "type": "land"
        },
        {
          "time": "2020.12",
          "value": 135472,
          "type": "estate"
        },
        {
          "time": "2021.01",
          "value": 245779,
          "type": "land"
        },
        {
          "time": "2021.01",
          "value": 638056,
          "type": "estate"
        },
        {
          "time": "2021.02",
          "value": 709403,
          "type": "land"
        },
        {
          "time": "2021.02",
          "value": 565642,
          "type": "estate"
        },
        {
          "time": "2021.03",
          "value": 3529714,
          "type": "land"
        },
        {
          "time": "2021.03",
          "value": 2425284,
          "type": "estate"
        },
        {
          "time": "2021.04",
          "value": 2489097,
          "type": "land"
        },
        {
          "time": "2021.04",
          "value": 3889673,
          "type": "estate"
        },
        {
          "time": "2021.05",
          "value": 1435325,
          "type": "land"
        },
        {
          "time": "2021.05",
          "value": 1651385,
          "type": "estate"
        },
        {
          "time": "2021.06",
          "value": 703143,
          "type": "land"
        },
        {
          "time": "2021.06",
          "value": 1905821,
          "type": "estate"
        },
        {
          "time": "2021.07",
          "value": 532034,
          "type": "land"
        },
        {
          "time": "2021.07",
          "value": 521230,
          "type": "estate"
        },
        {
          "time": "2021.08",
          "value": 794561,
          "type": "land"
        },
        {
          "time": "2021.08",
          "value": 1309768,
          "type": "estate"
        },
        {
          "time": "2021.09",
          "value": 1711352,
          "type": "land"
        },
        {
          "time": "2021.09",
          "value": 1483887,
          "type": "estate"
        },
        {
          "time": "2021.10",
          "value": 2088319,
          "type": "land"
        },
        {
          "time": "2021.10",
          "value": 2379460,
          "type": "estate"
        },
        {
          "time": "2021.11",
          "value": 10567284,
          "type": "land"
        },
        {
          "time": "2021.11",
          "value": 11427664,
          "type": "estate"
        },
        {
          "time": "2021.12",
          "value": 13462606,
          "type": "land"
        },
        {
          "time": "2021.12",
          "value": 11530122,
          "type": "estate"
        },
        {
          "time": "2022.01",
          "value": 8088046,
          "type": "land"
        },
        {
          "time": "2022.01",
          "value": 8819028,
          "type": "estate"
        },
        {
          "time": "2022.02",
          "value": 4620409,
          "type": "land"
        },
        {
          "time": "2022.02",
          "value": 5931991,
          "type": "estate"
        }
      ]
    }
  }
}
```
---
**6\.11 获取 Decentraland 地主总数统计信息接口**
###### 接口功能
> 获取 Decentraland 地主总数统计信息接口

###### URL
> https://api.metacat.world/api/v1/get_dcl_parcel_owner_stats

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
          "value": 0,
          "type": "all"
        },
        {
          "time": "2019.10",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2019.11",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2019.12",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.01",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.02",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.03",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.04",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.05",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.06",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.07",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.08",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.09",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.10",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.11",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2020.12",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.01",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.02",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.03",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.04",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.05",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.06",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.07",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.08",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.09",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.10",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.11",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2021.12",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2022.01",
          "value": 0,
          "type": "all"
        },
        {
          "time": "2022.02",
          "value": 5335,
          "type": "all"
        }
      ]
    }
  }
}
```
---
**7.1 获取钱包登录所需 nonce 接口**
###### 接口功能
> 获取钱包登录所需 nonce 接口

###### URL
> https://api.metacat.world/api/v1/user/get_nonce

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数    | 必选 |  类型  | 默认值 | 描述           |
| :------ | :--- | :----: | :----- | -------------- |
| address | true | string | 无     | 以太坊钱包地址 |

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/user/get_nonce?address=0xD67c34169b372d5B3932c548a940D4Ea74Fe7aF5' | jq .
```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "address": "0xd67c34169b372d5b3932c548a940d4ea74fe7af5",
    "nonce": "Hi from MetaCat! Sign this message to prove you have access to this wallet and we'll log you in. This won't cost you any Ether.\nFor enhanced security, here's a one-time code (no need to remember it): 39139878"
  }
}
```
---
**7.2 用户登录接口 **
###### 接口功能
> 对 nonce 签名后，请求的登录接口，登录成功返回 access_token 和 refresh_token
> **注：若接口返回数据中 profile 字段内容为空，则说明用户尚未设置基本信息**

###### URL
> https://api.metacat.world/api/v1/user/login_signature

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数      | 必选 |  类型  | 默认值 | 描述                    |
| :-------- | :--- | :----: | :----- | ----------------------- |
| address   | true | string | 无     | 用户钱包地址            |
| signature | true | string | 无     | 用户钱包对 nonce 的签名 |

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s -d 'address=0xD67c34169b372d5B3932c548a940D4Ea74Fe7aF5&signature=0xa63391de17be74963a077db91c92ec5244ca725275fa1d276cce17ee711061004d4abf1d424e24a35fdfbb60045e4c126452b18c70b77082694000c3d89320a11c' https://api.metacat.world/api/v1/user/login_signature | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTgyMjIyOTEsImZsYWciOjAsImlhdCI6MTYxODE5MzQ5MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.Bt7RJ4StnLBhbhP8tFCqUJ4RkPUmJyyP1nEY8HBCZnI",
    "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjA3ODU0OTEsImZsYWciOjEsImlhdCI6MTYxODE5MzQ5MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.2Vd9SnGHPtvlRvQay_I42vz1ADQGQJzm8Cz09EWAIAg",
    "profile": {
      "address": "0xD67c34169b372d5B3932c548a940D4Ea74Fe7aF5",
      "name": "k1ic",
      "avatar": "https://poster-phi.vercel.app/metacat_logo.png"
    }
  }
}
```
---
**7.3 用户登出接口 **
###### 接口功能
>

###### URL
> https://api.metacat.world/api/v1/user/logout

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 | 类型  | 默认值 | 描述              |
| :------------ | :--- | :---: | :----- | ----------------- |
| Header        |      |       |        | 请求报文头        |
| Authorization | true | sring | 无     | 值为 access_token |

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTc4MjAzMzksImZsYWciOjAsImlhdCI6MTYxNzc5MTUzOSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.bZf7nfyQdbndB4LJDYre06EFqcZzh4YFj1MBQQCxYWk' -d '' 'https://api.metacat.world/api/v1/user/logout' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**7.4 用户 access_token 刷新接口**

###### 接口功能
> 请求任何登录保护接口时，若接口返回 code: 100003，则表示 access_token 已过期；此时前端可通过 refresh_token 接口尝试获取新的 access_token，若该接口依然返回 code: 100003，则表示 refresh_token 也已过期，此时需再走一遍登录流程

###### URL
> https://api.metacat.world/api/v1/user/refresh_token

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述                                                                                                    |
| :------------ | :--- | :----: | :----- | ------------------------------------------------------------------------------------------------------- |
| refresh_token | true | string | 无     | 用于更新 access_token 的 refresh_token，首次登录时随 access_token 一起下发，但有效期比 refresh_token 长 |

###### 返回字段

| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s 'https://api.metacat.world/api/v1/user/refresh_token?refresh\_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjAzODI5OTEsImZsYWciOjEsImlhdCI6MTYxNzc5MDk5MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.B36i\_hZBVA\_AzpvOuK25r0tt0IoolXpOGWHxHs6bRng' | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTc4MjAzMzksImZsYWciOjAsImlhdCI6MTYxNzc5MTUzOSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.bZf7nfyQdbndB4LJDYre06EFqcZzh4YFj1MBQQCxYWk",
    "refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MjAzODI5OTEsImZsYWciOjEsImlhdCI6MTYxNzc5MDk5MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.B36i_hZBVA_AzpvOuK25r0tt0IoolXpOGWHxHs6bRng"
  }
}
```
---
**7.5 获取当前登录者基本信息接口**

###### 接口功能
> 需先登录

###### URL
> https://api.metacat.world/api/v1/user/get_base_info

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 | 类型  | 默认值 | 描述              |
| :------------ | :--- | :---: | :----- | ----------------- |
| Header        |      |       |        | 请求报文头        |
| Header.Authorization | true | sring | 无     | 值为 access_token |

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTc4ODUyNjEsImZsYWciOjAsImlhdCI6MTYxNzg1NjQ2MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.TdVCc49KR0gM3XspXp-afHuuIH0AfulXF0ZmBghrqf8' https://api.metacat.world/api/v1/user/get_base_info | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "profile": {
      "address": "0xd67c34169b372d5b3932c548a940d4ea74fe7af5",
      "nick_name": "k1ic",
      "avatar": "https://poster-phi.vercel.app/metacat_logo.png",
      "links": {
			"twitter_name": "Metacat007",
			"website_url": "https://www.k1ic.com/"
      }
    }
  }
}
```
---
**7.6 更新当前登录者基本信息接口**

###### 接口功能
> 仅限当前登录者修改自己的基本信息（**注：每次需全量传参**）

###### URL
> https://api.metacat.world/api/v1/user/update_base_info

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body          |      |        |        | 请求体            |
| Body.nick_name          | true | string | ‘’     | 用户昵称          |
| Body.twitter_name         | true | string | ‘’     | 用户twitter名称          |
| Body.website_url         | true | string | ‘’     | 用户个人站点链接          |
| Body.avatar         | true | string | ‘’     | 用户头像url         |

###### 返回字段
| 返回字段 | 字段类型 | 说明                                                     |
| :------- | :------- | :------------------------------------------------------- |
| code     | int      | 返回结果状态。100000：正常，其他：错误。详见“全局错误码” |
| msg      | string   | code 码为非 100000 时，对应的 error msg                  |
| data     | string   | 详见接口示例                                             |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTc4ODUyNjEsImZsYWciOjAsImlhdCI6MTYxNzg1NjQ2MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.TdVCc49KR0gM3XspXp-afHuuIH0AfulXF0ZmBghrqf8' -d 'nick_name=k1ic&twitter_name=Metacat007&website_url=https://www.k1ic.com/&avatar=https://s2.coinmarketcap.com/static/img/coins/64x64/6210.png' https://api.metacat.world/api/v1/user/update_base_info | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**7.7 获取当前登录者地块列表接口**

###### 接口功能
> 仅限获取当前登录者自己的地块列表

###### URL
> https://api.metacat.world/api/v1/user/get_parcel_list

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTc4ODUyNjEsImZsYWciOjAsImlhdCI6MTYxNzg1NjQ2MSwiaXNzIjoiYXJ0Z2VlIiwid2FsbGV0X2FkZHJlc3MiOiIweEQ2N2MzNDE2OWIzNzJkNUIzOTMyYzU0OGE5NDBENEVhNzRGZTdhRjUifQ.TdVCc49KR0gM3XspXp-afHuuIH0AfulXF0ZmBghrqf8' https://api.metacat.world/api/v1/user/get_parcel_list | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "cryptovoxels_parcel_list": [
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
    ],
    "decentraland_parcel_list": [
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
**7.8 判断 nick_name 是否已存在的接口**

###### 接口功能
> 

###### URL
> https://api.metacat.world/api/v1/user/is_nick_name_exist

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.nick_name | true | sring  | 无     | 必填 |

###### 接口示例
> curl -s https://api.metacat.world/api/v1/user/is_nick_name_exist?nick_nam='jobs' | jq .

```
{
  "code": 100006,
  "msg": "nick_name exist"
}
```
---
**8.1 获取当前登录者 Cryptovoxels 地块列表接口**

###### 接口功能
> 仅限获取当前登录者自己的地块列表

###### URL
> https://api.metacat.world/api/v1/rent/get_owned_cv_parcel_list

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/get_owned_cv_parcel_list | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": {
    "parcel_list": [
      {
        "parcel_id": 5701,
        "name": "MetaCat Firenze",
        "description": "# Metaverse Data Analytics & Content Navigation.\n## Website: [www.metacat.world](https://www.metacat.world/) Twitter: [@Metacat007](https://twitter.com/Metacat007) Medium: [@themetacat](https://medium.com/@themetacat)",
        "type": "Other",
        "cover_img_url": "https://media-crvox.sfo2.digitaloceanspaces.com/0xd30a79e487351eb0064c8a78eb341da364d78a9a/womps/1644892311425-85279617-f76a-43da-ac5b-9034bf8aed6d.jpg",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/5701",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/5701",
        "island": "Miami",
        "suburb": "Miami",
        "area": 129,
        "high": 17,
        "traffic": 1230,
        "price": 0.1,
        "status": "leased",
        "end_date": "2022.08.12",
        "is_built": "no"
      },
      {
        "parcel_id": 6616,
        "name": "MetaCat HQ",
        "description": "# Metaverse Data Analytics & Content Navigation.\n## Website: [www.metacat.world](https://www.metacat.world/) Twitter: [@Metacat007](https://twitter.com/Metacat007) Medium: [@themetacat](https://medium.com/@themetacat)",
        "type": "HQ",
        "cover_img_url": "",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/6616",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/6616",
        "island": "Scarcity",
        "suburb": "Bronze",
        "area": 195,
        "high": 13,
        "traffic": 1230,
        "price": 0.1,
        "status": "leased",
        "end_date": "2022.08.12",
        "is_built": "no"
      },
      {
        "parcel_id": 7246,
        "name": "None",
        "description": "None",
        "type": "Other",
        "cover_img_url": "",
        "opensea_url": "https://opensea.io/assets/0x79986aF15539de2db9A5086382daEdA917A9CF0C/7246",
        "parcel_page_url": "https://www.cryptovoxels.com/parcels/7246",
        "island": "Andromeda",
        "suburb": "Milky Way",
        "area": 527,
        "high": 8,
        "traffic": 1230,
        "price": 0.1,
        "status": "leased",
        "end_date": "2022.08.12",
        "is_built": "no"
      }
    ]
  }
}
```
---
**8.2 批量（单个）挂出 Cryptovoxels 待租地块接口**

###### 接口功能
> 仅限获取当前登录者，批量（单个）挂出自己拥有的 Cryptovoxels 地块

###### URL
> https://api.metacat.world/api/v1/rent/batch_list_cv_parcels

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.parcel_ids        |   true   |    sring   |    无    |  多个地块id用逗号分隔，如：5701,6616     |
| Body.is_built        |   true   |    sring    |    no   |   地块是否已建造：yes or no    |
| Body.price        |   true   |    float or int    |    0.1   |   地块租赁价格    |
| Body.start_at        |   true   |    int    |       |   地块可租开始时间，须大于等于当前时间，格式：1648121354    |
| Body.end_at        |   true   |    int    |       |   地块可租结束时间，须大于地块可租开始时间，格式：1656070154    |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/batch_list_cv_parcels -d 'parcel_ids=5701,6616&price=0.1&is_built=no&start_at=1648121354&end_at=1656070154' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**8.3 批量（单个）取消已挂出 Cryptovoxels 地块接口**

###### 接口功能
> 仅限获取当前登录者，批量（单个）取消自己拥有的已挂出 Cryptovoxels 地块

###### URL
> https://api.metacat.world/api/v1/rent/batch_cancel_listed_cv_parcels

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.parcel_ids        |   true   |    sring or int   |    无    |  多个地块id用逗号分隔，如：5701,6616     |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/batch_cancel_listed_cv_parcels -d 'parcel_ids=5701,6616' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**8.4 批量（单个）更新已挂出 Cryptovoxels 地块为租赁中接口**

###### 接口功能
> 仅限获取当前登录者，批量（单个）更新自己拥有的已挂出 Cryptovoxels 地块状态为租赁中

###### URL
> https://api.metacat.world/api/v1/rent/batch_lease_listed_cv_parcels

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.parcel_ids        |   true   |    sring or int   |    无    |  多个地块id用逗号分隔，如：5701,6616     |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/batch_lease_listed_cv_parcels -d 'parcel_ids=5701,6616' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**8.5 单个更新 Cryptovoxels 地块租赁信息接口**

###### 接口功能
> 仅限获取当前登录者，单个更新已挂出地块租赁信息

###### URL
> https://api.metacat.world/api/v1/rent/update_cv_parcel

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.parcel_id        |   true   |    int   |    无    |  地块id，如：5701    |
| Body.is_built        |   false   |    sring    |    no   |   地块是否已建造：yes or no    |
| Body.price        |   false   |    float or int    |    0.1   |   地块租赁价格    |
| Body.start_at        |   false   |    int    |       |   地块可租开始时间，须大于等于当前时间，格式：1648121354    |
| Body.end_at        |   false   |    int    |       |   地块可租结束时间，须大于地块可租开始时间，格式：1656070154    |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/update_cv_parcel -d 'parcel_id=5701&price=0.1&is_built=no&start_at=1648121354&end_at=1656070154' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**8.6 获取 Cryptovoxels 岛屿列表接口**

###### 接口功能
> 获取 Cryptovoxels 当前的所有岛屿信息

###### URL
> https://api.metacat.world/api/v1/get_cv_islands

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Body        |      |        |        | 请求体            |
| -        |   -   |    -   |    -    |  -    |

###### 接口示例
> curl -s ‘https://api.metacat.world/api/v1/get_cv_islands' | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": [
    {
      "id": 1,
      "name": "Origin City"
    },
    {
      "id": 2,
      "name": "Proxima"
    },
    {
      "id": 3,
      "name": "Ceres"
    },
    {
      "id": 4,
      "name": "Little Ceres"
    },
    {
      "id": 5,
      "name": "Trinity"
    },
    {
      "id": 6,
      "name": "The Bronx"
    },
    {
      "id": 7,
      "name": "Electron"
    },
    {
      "id": 8,
      "name": "Proton"
    },
    {
      "id": 9,
      "name": "Neutron"
    },
    {
      "id": 10,
      "name": "Euro"
    },
    {
      "id": 11,
      "name": "Tokyo"
    },
    {
      "id": 12,
      "name": "Berlin"
    },
    {
      "id": 13,
      "name": "Helios"
    },
    {
      "id": 14,
      "name": "Milan"
    },
    {
      "id": 15,
      "name": "Poneke"
    },
    {
      "id": 16,
      "name": "San Francisco"
    },
    {
      "id": 17,
      "name": "Far Far Away"
    },
    {
      "id": 18,
      "name": "Vibes"
    },
    {
      "id": 19,
      "name": "Test Island"
    },
    {
      "id": 20,
      "name": "Satoshi"
    },
    {
      "id": 21,
      "name": "Miami"
    },
    {
      "id": 22,
      "name": "München"
    },
    {
      "id": 23,
      "name": "新宿区"
    },
    {
      "id": 24,
      "name": "서울"
    },
    {
      "id": 26,
      "name": "Pluto"
    },
    {
      "id": 27,
      "name": "Igloo"
    },
    {
      "id": 28,
      "name": "Honolulu"
    },
    {
      "id": 29,
      "name": "Pilikai"
    },
    {
      "id": 30,
      "name": "Kauai"
    },
    {
      "id": 31,
      "name": "Scarcity"
    },
    {
      "id": 33,
      "name": "Flora"
    },
    {
      "id": 34,
      "name": "Fauna"
    },
    {
      "id": 35,
      "name": "Andromeda"
    }
  ]
}
```
**8.7 单个更新租赁中 Cryptovoxels 地块为已挂出状态接口**

###### 接口功能
> 仅限获取当前登录者，单个更新自己拥有的租赁中 Cryptovoxels 地块状态为已挂出状态

###### URL
> https://api.metacat.world/api/v1/rent/cv_parcel_fallback_to_listed_status

###### 支持格式
> JSON

###### HTTP 请求方式
> POST

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Header        |      |        |        | 请求头            |
| Header.Authorization | true | sring  | 无     | 值为 access_token |
| Body        |      |        |        | 请求体            |
| Body.parcel_ids        |   true   |    sring or int   |    无    |  多个地块id用逗号分隔，如：5701,6616     |

###### 接口示例
> curl -s -H 'Authorization:eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2NDc4NzU0NTQsImZsYWciOjAsImlhdCI6MTY0Nzg0NjY1NCwiaXNzIjoibWV0YWNhdCIsIndhbGxldF9hZGRyZXNzIjoiMHgzOEJiRDM3NWQ0OWQ2MjM3OTg0Y2JmYTE5NzE5YzQxOWFmOUZFNTE0In0.cu98LvoCovuPh9Xm9I-LfrXCSgXhvfQsbhENO-ZJiI8' https://api.metacat.world/api/v1/rent/cv_parcel_fallback_to_listed_status -d 'parcel_id=5701' | jq .

```
{
  "code": 100000,
  "msg": "success"
}
```
---
**9.1 获取 OKX Wearable 列表页数据接口**

###### 接口功能
> 一次返回列表中全部数据

###### URL
> https://api.metacat.world/api/v1/wearable/get_okx_wearable_list

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Body        |      |        |        | 请求体            |
| -        |    -  |     -   |     -   | -           |


###### 接口示例
> curl -s https://api.metacat.world/api/v1/wearable/get_okx_wearable_list | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": [
    {
      "kol": {
        "name": "比特币子琪",
        "title": "子棋-热搜点评员",
        "desc": "微博@公众号：子棋-热搜点评员 专注行情分析，挖掘优质项目！ Weibo and WeChat public account: Bitcoin Ziqi, focusing on market analysis,discover high-quality projects. #BTC $ETH",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/BTC521.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/BTC521.vox",
        "opensea_url": "https://opensea.io/assets/matic/0x469da19448b0fafcf781350efcd5a09267ca1f99/60",
        "contact": {
          "twitter": "https://twitter.com/BTC521",
          "weibo": "https://weibo.com/u/6201825184"
        }
      },
      "artist": {
        "name": "Angelica",
        "website": "https://opensea.io/XUECHUN"
      },
      "id": 100
    },
    {
      "kol": {
        "name": "MetaCat",
        "title": "",
        "desc": "MetaCat focuses on metaverse data analysis, content navigation, and land leasing. The official website www.metacat.world launched in December 2021. It started to provide data services such as Metaverse Monthly Report in Q3 of 2021. MetaCat is one of Co-founders of  WearableDao, which dedicated to solving the problem of dressing in the metaverse.",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/MetaCat.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/MetaCat.vox",
        "opensea_url": "https://opensea.io/assets/matic/0xb7469e28640bed0d7155f3ac220c240f4fdee0ec/29",
        "contact": {
          "twitter": "https://twitter.com/MetaCat007",
          "weibo": "https://weibo.com/u/6104067155"
        }
      },
      "artist": {
        "name": "WackoZacco",
        "website": "https://opensea.io/WackoZacco"
      },
      "id": 101
    },
    {
      "kol": {
        "name": "杰尼龟",
        "title": "",
        "desc": "",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/Squirtle.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/Squirtle.vox",
        "opensea_url": "https://opensea.io/assets/matic/0xb7469e28640bed0d7155f3ac220c240f4fdee0ec/29",
        "contact": {
          "twitter": "",
          "weibo": ""
        }
      },
      "artist": {
        "name": "MERMAID",
        "website": ""
      },
      "id": 102
    },
    {
      "kol": {
        "name": "牛静熊动",
        "title": "",
        "desc": "",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/niujingxiongdong.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/niujingxiongdong.vox",
        "opensea_url": "https://opensea.io/assets/matic/0xb7469e28640bed0d7155f3ac220c240f4fdee0ec/29",
        "contact": {
          "twitter": "",
          "weibo": ""
        }
      },
      "artist": {
        "name": "丁棟樑",
        "website": ""
      },
      "id": 103
    },
    {
      "kol": {
        "name": "张力",
        "title": "",
        "desc": "",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/zhangli.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/zhangli.vox",
        "opensea_url": "https://opensea.io/assets/matic/0xb7469e28640bed0d7155f3ac220c240f4fdee0ec/29",
        "contact": {
          "twitter": "",
          "weibo": ""
        }
      },
      "artist": {
        "name": "熊诗怡",
        "website": ""
      },
      "id": 104
    },
    {
      "kol": {
        "name": "孙宇晨",
        "title": "",
        "desc": "",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/sunyuchentron.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/sunyuchentron.vox",
        "opensea_url": "https://opensea.io/assets/matic/0xb7469e28640bed0d7155f3ac220c240f4fdee0ec/29",
        "contact": {
          "twitter": "https://twitter.com/sunyuchentron",
          "weibo": ""
        }
      },
      "artist": {
        "name": "MERMAID",
        "website": ""
      },
      "id": 105
    }
  ]
}
```
---
**9.2 获取 OKX Wearable 详情页数据接口 **

###### 接口功能
> 通过id获取 OKX Wearable 详情

###### URL
> https://api.metacat.world/api/v1/wearable/get_okx_wearable_detail

###### 支持格式
> JSON

###### HTTP 请求方式
> GET

###### 请求参数
| 参数          | 必选 |  类型  | 默认值 | 描述              |
| :------------ | :--- | :----: | :----- | ----------------- |
| Body        |      |        |        | 请求体            |
| Body.id        |    true  |    int  |     -   |      |


###### 接口示例
> curl -s https://api.metacat.world/api/v1/wearable/get_okx_wearable_detail?id=100 | jq .

```
{
  "code": 100000,
  "msg": "success",
  "data": [
    {
      "kol": {
        "name": "比特币子琪",
        "title": "子棋-热搜点评员",
        "desc": "微博@公众号：子棋-热搜点评员 专注行情分析，挖掘优质项目！ Weibo and WeChat public account: Bitcoin Ziqi, focusing on market analysis,discover high-quality projects. #BTC $ETH",
        "d2_url": "https://poster-phi.vercel.app/wearable/okx/BTC521.png",
        "d3_url": "https://poster-phi.vercel.app/wearable/okx/BTC521.vox",
        "opensea_url": "https://opensea.io/assets/matic/0x469da19448b0fafcf781350efcd5a09267ca1f99/60",
        "contact": {
          "twitter": "https://twitter.com/BTC521",
          "weibo": "https://weibo.com/u/6201825184"
        }
      },
      "artist": {
        "name": "Angelica",
        "website": "https://opensea.io/XUECHUN"
      },
      "id": 100
    }
  ]
}
```