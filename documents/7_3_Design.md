---
style: default
title: API设计
---

# 7.3 API设计

### 返回码

| Code |               Description                |
| :--: | :--------------------------------------: |
| 200  |                 success                  |
| 401  | log in fail -- username not exist/ password incorrect |
| 402  |  register fail -- username/phone exists  |
|      |                                          |
|      |                                          |

### 用户类

#### 获取用户信息

```
GET /resource/users/{id}
```

#### Response

```
{
    "userId": "112233",
    "username": "dramaQueen",
    "phone": "12345678910"
}
```



#### 用户登录

```
POST /resource/users/{username}
```

#### Response

```
{
    "code": "200",
    "userId": "334455"
}
```

#### 用户登出

```
POST /resource/users/{userId}
```

#### Response

```
{
    "code":"200",
    "userId":"334455"
}
```

#### 用户注册

```
POST /resource/users
```

#### Response

```
{
    "code": "402",
    "log": "register phone exists"
}
```



### 电影类

#### 获取电影信息

```
GET /resource/movie/{movieId}
```

#### Response

```
{
    "movieId": 002,
    "movieName": "复仇者联盟3",
    "type": ["科幻","动作"],
    "pubDate": "2018-05-11",
    "length": 150,
    "status": "on",
    "director": "安东尼·罗素",
    "starring": ["小罗伯特·唐尼","乔什·布洛林","斯嘉丽·约翰逊"]
}
```

#### 获取电影海报

```
GET /resource/moviePoster/{movieId}
```

#### Response

```
{
    "poster": "http://123.123.123.123/XXX.png"
}
```



### 影院类

#### 获取电影院信息

```
GET /resource/cinema/{cinemaId}
```

#### Response

```
{
    "cinemaId": 001,
    "cinemaName": "金逸珠江国际影城（大学城店）",
    "address": "番禺区大学城GOGO新天地2期XX铺"
}
```



#### 获取影厅信息

```
GET /resource/cinema/{cinemaId}/hall/{hallId}
```

#### Response

```
{
    "cinemaId": 001,
    "cinemaName": "金逸珠江国际影城（大学城店）",
    "hallId": "1"
    "seatRowNumber": "10"
    "sertColNumber": "13"
}
```

#### 获取座位信息信息

```
GET /resource/cinema/{cinemaId}/hall/{hallId}/{seat}
```

#### Response

```
{
    "token": "No"
}
```



### 电影排期类

#### 获得某场次电影信息

```
GET /resource/cinema/{cinemaId}/movie-session/{sessionId}
```

#### Response

```
{
    "sessionId": "10289234",
    "cinemaId": 001,
    "cinemaName": "金逸珠江国际影城（大学城店）",
    "hallId": "1",
    "movieName": "复仇者联盟3",
    "showDate": "2018-05-11",
    "showTime": "13:05:00"
}
```



### 电影票类

#### 获得电影票信息

```
GET /resource/tickets/{ticketId}
```

#### Response

```
{
    "ticketId": "23048022323434",
    "userId": "112233"
    "cinemaId": 001,
    "cinemaName": "金逸珠江国际影城（大学城店）",
    "hallId": "1",
    "movieName": "复仇者联盟3",
    "showDate": "2018-05-11",
    "showTime": "13:05:00",
    "consumeDate": "2018-05-10",
    "consumeTime": "23:30:00"
}
```

#### 获取用户购票记录

```
GET /resource/users/{userId}/tickets
```

#### Response

```
{
    "userId": "112233"
    "ticketsIds": ["23048022323434","23894329384329","43984954375712"]
}
```

#### 获取取票信息

```
GET /resource/tickets/{ticketId}/extraction
```

#### Response

```
{
    "ticketsIds": "23048022323434"
    "serialNumber": "904820"
    "codeNumber"" "059403"
}
```