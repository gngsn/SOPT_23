# URI & API 과제



## Pokemon 도감 URI

| 메소드 | 경로                    | 설명      |
| ------ | ----------------------- | --------- |
| GET    | /pokemons/{pokemon_idx} | 도감 조희 |
| POST   | /pokemons               | 도감 등록 |
| PUT    | /pokemons/{pokemon_idx} | 도감 수정 |
| DELETE | /pokemons/{pokemon_idx} | 도감 삭제 |





---



## 도감 조회

| 메소드 | 경로                    | 짧은 설명 |
| ------ | ----------------------- | --------- |
| GET    | /pokemons/{pokemon_idx} | 도감 조회 |

### 요청 헤더

```
content-Type : multipart/form-data
```



### 응답 바디

#### 응답 성공

```
{
    "status" : 200,
    "message" : "조회 성공",
    "data" : {
        "name" : "피카츄",
        "type" : "전기 포켓몬",
        "height" : "0.4cm",
        "weight" : "6.0kg",
        "auth" : false,
        "like" : true,
    }
}
```

#### 없는 조회

```
{
    "status" : 404,
    "message" : "존재하지 않는 포켓몬입니다.",
    "data" : null
}
```

#### 서버 내부 에러

```
{
    "status" : 500,
    "message" : "서버 내부에 문제가 있습니다.",
    "data" : null
}
```



------



## 도감 등록

| 메소드 | 경로      | 짧은 설명 |
| ------ | --------- | --------- |
| POST   | /pokemons | 도감 등록 |



### 요청 헤더

```
content-Type : multipart/form-data
```



### 요청 바디

```
{
    "name" : "피카츄",
    "type" : "전기",
    "photo" : "사진 객체"
}
```



###  응답 바디

#### 응답 성공

```
{
    "status" : 201,
    "message" : "등록 성공",
    "data" : null
}
```

#### 등록 실패

```
{
    "status" : 400,
    "message" : "등록 실패",
    "data" : null
}
```

#### DB 에러

```
{
    "status" : 600,
    "message" : "데이터 베이스 에러",
    "data" : null
}
```



---

## 도감 수정

| 메소드 | 경로                    | 짧은 설명 |
| ------ | ----------------------- | --------- |
| PUT    | /pokemons/{pokemon_idx} | 도감 수정 |

### 요청 헤더

```
content-Type : multipart/form-data
```



### 요청 바디

```
{
	"type" : "전기 쥐포켓몬",
    "weight" : "10.0kg"
}
```



### 응답 바디

#### 응답 성공

```
{
    "status" : 201,
    "message" : "수정에 성공했습니다."
    "data" : {
		"type" : "전기 쥐포켓몬",
  	  "weight" : "10.0kg"
	}
}
```



#### 수정 실패

```
{
    "status" : 400,
    "message" : "수정에 실패했습니다."
    "data" : null
}
```

#### 인증 실패

```
{
    "status" : 401,
    "message" : "권한이 없습니다."
    "data" : null
}
```

#### DB 저장 실패

```
{
    "status" : 404,
    "message" : "데이터 저장에 실패했습니다."
    "data" : null
}
```

#### 서버 내부 에러

```
{
    "status" : 500,
    "message" : "서버 내부에 문제가 있습니다."
    "data" : null
}
```



---

## 도감 삭제

| 메소드 | 경로                    | 짧은 설명 |
| ------ | ----------------------- | --------- |
| DELETE | /pokemons/{pokemon_idx} | 도감 삭제 |

### 요청 헤더

```
content-Type : multipart/form-data
```



### 응답 바디

#### 글 삭제 성공

```
{
    "status": 204,
    "message": "삭제 성공",
    "data": null
}
```

#### 다른 회원의 글 삭제 시도

```
{
    "status": 403,
    "message": "권한이 없습니다.",
    "data": false
}
```

#### 없는 글 삭제

```
{
    "status": 404,
    "message": "존재하지 않는 포켓몬입니다.",
    "data": null
}
```

#### 인증 실패

```
{
    "status": 401,
    "message": "인증 실패",
    "data": null
}
```

#### DB 에러

```
{
    "status": 600,
    "message": "데이터베이스 에러",
    "data": null
}
```

#### INTERNAL SERVER ERROR

```
{
    "status": 500,
    "message": "서버 내부 에러",
    "data": null
}
```
