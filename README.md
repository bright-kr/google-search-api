# Google Search API

[![Promo](https://media.brightdata.com/2025/08/SERP-API-50-off-GitHub-banner_1389_166.png)](https://brightdata.co.kr/products/serp-api/google-search) 

> ⚠️ 2025년 1월 기준으로, [Google은 JavaScript를 요구합니다](https://techcrunch.com/2025/01/17/google-begins-requiring-javascript-for-google-search/). 이는 검색 결과를 렌더링하기 위함입니다. 이 업데이트는 비 JavaScript 기반 방식에 의존하는 기존 봇, 스クレイピング 도구, SEO 도구를 차단하는 것을 목표로 합니다. 그 결과, 시장 조사 또는 순위 분석을 위해 Google Search를 사용하는 기업은 JavaScript 렌더링을 지원하는 도구를 채택해야 합니다.


이 리포지토리는 Google SERP 데이터를 수집하기 위한 두 가지 접근 방식을 제공합니다:

1. 기본 데이터 수집에 적합한 무료 소규모 스크레이퍼
2. 대량 처리 및 견고한 데이터 요구 사항을 위해 구축된 엔터프라이즈급 API 솔루션


## Table of Contents
- [Free Scraper](#free-scraper)
  - [Input Parameters](#input-parameters)
  - [Implementation](#implementation)
  - [Sample Output](#sample-output)
  - [Limitations](#limitations)
- [Bright Data Google Search API](#bright-data-google-search-api)
  - [Key Features](#key-features)
  - [Getting Started](#getting-started)
  - [Direct API Access](#direct-api-access)
  - [Native Proxy-Based Access](#native-proxy-based-access)
- [Advanced Features](#advanced-features)
  - [Localization](#localization)
  - [Search Type](#search-type)
  - [Pagination](#pagination)
  - [Geo-Location](#geo-location)
  - [Device Type](#device-type)
  - [Browser Type](#browser-type)
  - [Parsing Results](#parsing-results)
  - [Hotel Search](#hotel-search)
  - [Parallel Searches](#parallel-searches)
  - [AI Overview](#ai-overview)
- [Support & Resources](#support--resources)


## Free Scraper
기본 데이터 수집 요구 사항을 위한 경량 Google 스크레이퍼입니다.

<img width="700" alt="google-search-result" src="https://github.com/bright-kr/google-search-api/blob/main/images/416310595-58573147-5ac2-4cb3-bb5e-295d76f6972c.png" />

### Input Parameters

- **File:** Google에 쿼리할 검색어 목록(필수)
- **Pages:** 데이터를 스크레이핑할 Google 페이지 수

### Implementation
[Python file](https://github.com/bright-kr/Google-Search-API/blob/main/free_google_scraper/google_serp.py)에서 다음 파라미터를 수정합니다:

```python
HEADLESS = False        
MAX_RETRIES = 2         
REQUEST_DELAY = (1, 4) 

SEARCH_TERMS = [
    "nike shoes",
    "macbook pro"
]
PAGES_PER_TERM = 3      
```

💡 **Tip:** Google의 탐지 메커니즘을 피하는 데 도움이 되도록 `HEADLESS = False`로 설정합니다.

### Sample Output
<img width="700" alt="google-serp-data" src="https://github.com/bright-kr/google-search-api/blob/main/images/416109839-c7048fc9-44c3-4553-8117-2b238d354f70.png" />


### Limitations

Google은 여러 앤치봇 조치를 구현합니다:

1. **CAPTCHAs:** 사람과 봇을 구분하는 데 사용됩니다
2. **IP Blocks:** 의심스러운 활동에 대해 일시적 또는 영구적 차단이 적용됩니다
3. **Rate Limiting:** 빠른 리クエスト는 차단을 유발할 수 있습니다
4. **Geotargeting:** 결과는 위치, 언어, 디바이스에 따라 달라집니다
5. **Honeypot Traps:** 자동화된 접근을 감지하기 위한 숨겨진 요소입니다

여러 번 리クエ스트를 보내면 Google의 CAPTCHA 챌린지에 직면할 가능성이 큽니다:

<img width="700" alt="google-captcha" src="https://github.com/bright-kr/google-search-api/blob/main/images/414117571-21ab3e9f-1162-4aef-9e22-fb08491dd928.png" />

## Bright Data Google Search API
[Bright Data's Google Search API](https://brightdata.co.kr/products/serp-api/google-search)는 커스터마이즈 가능한 검색 파라미터를 사용하여 Google에서 실제 사용자 검색 결과를 제공합니다. 동일한 고급 기술을 기반으로 하는 [SERP API](https://brightdata.co.kr/products/serp-api)와 마찬가지로, 공개적으로 이용 가능한 데이터를 대규모로 스크레이핑할 때 높은 성공률과 견고한 성능을 제공합니다.


### Key Features

- 대량 처리에서도 높은 성공률
- 성공한 리クエ스트에 대해서만 과금
- 빠른 응답 시간 - 5초 미만
- 지오로케이션 타겟팅 – 모든 국가, 도시 또는 디바이스에서 데이터 추출
- 출력 형식 – JSON 또는 raw HTML로 데이터 수신
- 다양한 검색 유형 – 뉴스, 이미지, 쇼핑, 채용 등
- 비동기 리クエ스트 – 배치로 결과 가져오기
- 대규모 처리에 최적화 – 높은 트래픽 및 피크 로드 처리

📌 [SERP Playground](https://brightdata.co.kr/products/serp-api/google-search)에서 무료로 테스트해 보실 수 있습니다:

<img width="700" alt="bright-data-serp-api-playground" src="https://github.com/bright-kr/google-search-api/blob/main/images/416966701-8d516e08-37a1-4723-bf12-9a9da6a13b1a.png" />


### Getting Started

1. **Prerequisites:**
    - [Bright Data account](https://brightdata.co.kr/)를 생성합니다(신규 사용자는 $5 크레딧을 받습니다)
    - [API key](https://docs.brightdata.com/general/account/api-token)를 발급받습니다
2. **Setup:** [step-by-step guide](https://github.com/bright-kr/Google-Search-API/blob/main/setup_serp_api.md)를 따라 Bright Data 계정에 SERP API를 통합합니다
3. **Implementation Methods:**
    - Direct API Access
    - Native Proxy-Based Access


### Direct API Access
가장 간단한 방법은 API에 직접 리クエ스트를 보내는 것입니다.

**cURL Example**
```bash
curl https://api.brightdata.com/request \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d '{
        "zone": "ZONE_NAME",
        "url": "https://www.google.com/search?q=ollama&brd_json=1",
        "format": "raw"
      }'
```

**Python Example**
```python
import requests
import json

url = "https://api.brightdata.com/request"

headers = {"Content-Type": "application/json", "Authorization": "Bearer API_TOKEN"}

payload = {
    "zone": "ZONE_NAME",
    "url": "https://www.google.com/search?q=ollama&brd_json=1",
    "format": "raw",
}

response = requests.post(url, headers=headers, json=payload)

with open("serp_direct_api.json", "w") as file:
    json.dump(response.json(), file, indent=4)

print("Response saved to 'serp_direct_api.json'.")
```

👉 [full JSON output](https://github.com/bright-kr/Google-Search-API/blob/main/google_search_api_outputs/serp_direct_api.json) 보기

> **Note**: 파싱된 JSON의 경우 `brd_json=1`을 사용하고, 파싱된 JSON + 전체 중첩 HTML의 경우 `brd_json=html`을 사용합니다.

검색 결과 파싱에 대해 더 알아보려면 [SERP API Parsing Guide](https://docs.brightdata.com/scraping-automation/serp-api/parsing-search-results)를 확인하십시오.

### Native Proxy-Based Access
대신 프록시 라우팅 방식을 사용할 수도 있습니다.

**cURL Example**
```bash
curl -i \
  --proxy brd.superproxy.io:33335 \
  --proxy-user "brd-customer-<CUSTOMER_ID>-zone-<ZONE_NAME>:<ZONE_PASSWORD>" \
  -k \
  "https://www.google.com/search?q=ollama"
```

**Python Example**
```python
import requests
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

host = "brd.superproxy.io"
port = 33335
username = "brd-customer-<customer_id>-zone-<zone_name>"
password = "<zone_password>"
proxy_url = f"http://{username}:{password}@{host}:{port}"

proxies = {"http": proxy_url, "https": proxy_url}

url = "https://www.google.com/search?q=ollama"
response = requests.get(url, proxies=proxies, verify=False)

with open("serp_native_proxy.html", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved to 'serp_native_proxy.html'.")
```

👉 [full HTML output](https://github.com/bright-kr/Google-Search-API/blob/main/google_search_api_outputs/serp_native_proxy.html) 보기

프로덕션 환경에서는 Bright Data의 SSL 인증서를 로드하십시오([SSL Certificate Guide](https://docs.brightdata.com/general/account/ssl-certificate) 참조).

## Advanced Features

### Localization
<img width="700" alt="bright-data-google-search-api-screenshot-localization" src="https://github.com/bright-kr/google-search-api/blob/main/images/416281053-eb050c00-3c35-451b-a2d2-e98e16f91aee.png" />


1. `gl` (Country Code)
    - 검색 결과의 국가를 결정하는 두 글자 국가 코드입니다
    - 특정 국가에서 수행된 것처럼 검색을 시뮬레이션합니다
    
    Example: 프랑스에서 레스토랑 검색
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+restaurants+in+paris&gl=fr"
    ```
    
2. `hl` (Language Code)
    - 페이지 콘텐츠의 언어를 설정하는 두 글자 언어 코드입니다
    - 인터페이스 및 검색 결과 언어에 영향을 줍니다
    
    Example: 일본에서 스시 레스토랑 검색(결과는 일본어)
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+sushi+restaurants+in+tokyo&hl=ja"
    ```
    
    더 나은 로컬라이제이션을 위해 두 파라미터를 함께 사용할 수 있습니다:
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+hotels+in+berlin&gl=de&hl=de"
    ```

### Search Type
<img width="700" alt="bright-data-google-search-api-screenshot-search-type" src="https://github.com/bright-kr/google-search-api/blob/main/images/416280410-49853108-5e3d-4062-831b-8d55711d5f54.png" />

1. `tbm` (Search Category)
    - 특정 검색 유형(이미지, 뉴스 등)을 지정합니다
    - **Options**:
        - `tbm=isch` → **Images**
        - `tbm=shop` → **Shopping**
        - `tbm=nws` → **News**
        - `tbm=vid` → **Videos**
    
    **Example** (Shopping 검색):
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=macbook+pro&tbm=shop"
    ```
    
2. `ibp` (Jobs Search Parameter)
    - 채용 관련 검색에 대해 특히 사용합니다
    - Example: `ibp=htl;jobs`는 채용 목록을 반환합니다
    
    **Example**:
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=technical+copywriter&ibp=htl;jobs"
    ```

### Pagination

결과 페이지를 이동하거나 표시되는 결과 수를 조정합니다:

1. `start`
    - 검색 결과의 시작 지점을 정의합니다
    - Examples:
        - `start=0` (default) - 첫 페이지
        - `start=10` - 두 번째 페이지(결과 11-20)
        - `start=20` - 세 번째 페이지(결과 21-30)
    
    **Example** (11번째 결과부터 시작):
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=best+coding+laptops+2025&start=10"
    ```
    
2. `num`
    - 페이지당 반환할 결과 수를 정의합니다
    - Examples:
        - `num=10` (default) - 10개 결과를 반환합니다
        - `num=50` - 50개 결과를 반환합니다
    
    **Example** (40개 결과 반환):
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=best+coding+laptops+2025&num=40"
    ```


### Geo-Location
<img width="700" alt="bright-data-google-search-api-screenshot-geolocation" src="https://github.com/bright-kr/google-search-api/blob/main/images/416279186-af64c770-0c8a-4007-9415-304d2e0c0fe8.png" />

`uule` 파라미터는 특정 위치를 기준으로 검색 결과를 커스터마이즈합니다:

- 일반 텍스트가 아니라 인코딩된 문자열이 필요합니다.
- [Google's geotargeting CSV](https://developers.google.com/adwords/api/docs/appendix/geotargeting)의 Canonical Name 열에서 원본 위치 문자열을 찾습니다.
- 서드파티 컨버터 또는 내장 라이브러리를 사용하여 원본 문자열을 인코딩 형식으로 변환합니다.
- API 리クエ스트에 `uule` 값으로 인코딩된 문자열을 포함합니다.

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+hotels+in+paris&uule=w+CAIQICIGUGFyaXM"
```

### Device Type

<img width="700" alt="bright-data-google-search-api-screenshot-device-type" src="https://github.com/bright-kr/google-search-api/blob/main/images/416278511-cf0f203f-5d62-4eb9-9d28-7a50d75c7a00.png" />


`brd_mobile` 파라미터를 사용하여 특정 디바이스에서의 리クエ스트를 시뮬레이션합니다:

| Value | Device | User-Agent Type |
| --- | --- | --- |
| `0` or omit | Desktop | Desktop |
| `1` | Mobile | Mobile |
| `ios` or `iphone` | iPhone | iOS |
| `ipad` or `ios_tablet` | iPad | iOS Tablet |
| `android` | Android | Android |
| `android_tablet` | Android Tablet | Android Tablet |

**Example: Mobile Search**

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+laptops&brd_mobile=1"
```

### Browser Type
<img width="700" alt="bright-data-google-search-api-screenshot-browser-type" src="https://github.com/bright-kr/google-search-api/blob/main/images/416277969-df382cb0-0eb2-4fb1-982c-2fa3401cc83a.png" />

`brd_browser` 파라미터를 사용하여 특정 브라우저에서의 리クエ스트를 시뮬레이션합니다:

- `brd_browser=chrome` — Google Chrome
- `brd_browser=safari` — Safari
- `brd_browser=firefox` — Mozilla Firefox (`brd_mobile=1`과 호환되지 않음)

지정하지 않으면 API는 랜덤 브라우저를 사용합니다.

**Example**:

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+gaming+laptops&brd_browser=chrome"
```

**Example** (브라우저 및 디바이스 유형 결합):

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+smartphones&brd_browser=safari&brd_mobile=ios"
```

### Parsing Results

`brd_json` 파라미터를 사용하여 구조화된 형식으로 검색 결과를 받습니다:

- **Options**:
    - `brd_json=1` - 파싱된 JSON 형식으로 결과를 반환합니다
    - `brd_json=html` - raw HTML을 포함하는 추가 `"html"` 필드가 있는 JSON을 반환합니다

Example (JSON output):

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=best+hotels+in+new+york&brd_json=1"
```

Example (raw HTML 포함 JSON):

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=top+restaurants+in+paris&brd_json=html"
```

자세한 내용은 [SERP API Parsing Guide](https://docs.brightdata.com/scraping-automation/serp-api/parsing-search-results)에서 확인하십시오.


### Hotel Search

<img width="700" alt="bright-data-google-search-api-screenshot-google-hotels-search" src="https://github.com/bright-kr/google-search-api/blob/main/images/416277071-0859191a-47c0-4373-b3af-a1bc04ea54b1.png" />


다음 파라미터로 호텔 검색을 세부 조정합니다:

1. `hotel_occupancy` (Number of Guests)
    - 투숙객 수를 설정합니다(최대 4명)
    - Examples:
        - `hotel_occupancy=1` → 1명
        - `hotel_occupancy=2` → 2명(기본값)
        - `hotel_occupancy=4` → 4명
    
    **Example** (뉴욕에서 4명 기준으로 호텔 검색):
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=hotels+in+new+york&hotel_occupancy=4"
    ```
    
2. `hotel_dates` (Check-in & Check-out Dates)
    - 특정 날짜 범위로 결과를 필터링합니다
    - Format: YYYY-MM-DD, YYYY-MM-DD
    
    **Example** (2025년 5월 1일부터 5월 3일까지 파리 호텔 검색):
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=hotels+in+paris&hotel_dates=2025-05-01%2C2025-05-03"
    ```
    
    **Combined Example**:
    
    ```bash
    curl --proxy brd.superproxy.io:33335 \
         --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
         "https://www.google.com/search?q=hotels+in+tokyo&hotel_occupancy=2&hotel_dates=2025-05-01%2C2025-05-03"
    ```

### Parallel Searches

동일한 peer 및 세ッション 내에서 여러 검색 리クエ스트를 동시에 전송할 수 있으며, 결과 비교에 이상적입니다.

1. 검색 변형을 포함하는 `multi` 배열로 POST 리クエ스트를 전송합니다
2. 이후 결과 조회를 위해 `response_id`를 받습니다
3. 처리가 완료되면 `response_id`를 사용하여 결과를 조회합니다

**Step 1: Send Parallel Requests**

```bash
RESPONSE_ID=$(curl -i --silent --compressed \
  "https://api.brightdata.com/serp/req?customer=<customer-id>&zone=<zone-name>" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d $'{
    "country": "us",
    "multi": [
      {"query": {"q": "top+macbook+for+developers", "num": 20}},
      {"query": {"q": "top+macbook+for+developers", "num": 100}}
    ]
  }' | sed -En 's/^x-response-id: (.*)/\1/p' | tr -d '\r')

echo "Response ID: $RESPONSE_ID"
```

**Step 2: Fetch Results**

```bash
curl -v --compressed \
     "https://api.brightdata.com/serp/get_result?customer=<customer-id>&zone=<zone-name>&response_id=${RESPONSE_ID}" \
     -H "Authorization: Bearer API_TOKEN"
```

또한 하나의 리クエ스트로 여러 키워드를 검색할 수도 있습니다:

```bash
{
  "multi":[
    {"query":{"q":"best+smartphones+2025"}},
    {"query":{"q":"best+laptops+2025"}}
  ]
}
```

비동기 리クエ스트에 대해 더 알아보려면 [here](https://docs.brightdata.com/scraping-automation/serp-api/asynchronous-requests)를 확인하십시오.

### AI Overview

<img width="700" alt="bright-data-google-search-api-screenshot-google-ai-overview" src="https://github.com/bright-kr/google-search-api/blob/main/images/416276209-3c7be724-e8d9-45ed-b781-017b1cbec9d4.png" />

Google은 때때로 검색 결과 상단에 AI 생성 요약(AI Overviews)을 포함합니다. 이러한 AI 생성 오버뷰를 볼 가능성을 높이려면 `brd_ai_mode=1`을 사용하십시오:

```bash
curl --proxy brd.superproxy.io:33335 \
     --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
     "https://www.google.com/search?q=how+does+caffeine+affect+sleep&brd_ai_mode=1"
```


## Support & Resources

- **Documentation:** [SERP API Docs](https://docs.brightdata.com/scraping-automation/serp-api/)
- **SEO Use Cases:** [SEO Tracking and Insights](https://brightdata.co.kr/use-cases/serp-tracking)
- **Other Guides:**
    - [SERP API](https://github.com/bright-kr/serp-api)
    - [Web Unlocker API](https://github.com/bright-kr/web-unlocker-api)
    - [Google Maps Scraper](https://github.com/bright-kr/Google-Maps-Scraper)
    - [Google News Scraper](https://github.com/bright-kr/Google-News-Scraper)
- **Interesting Reads:**
    - [Best SERP APIs](https://brightdata.co.kr/blog/web-data/best-serp-apis)
    - [Build a RAG Chatbot with SERP API](https://brightdata.co.kr/blog/web-data/build-a-rag-chatbot)
    - [Scrape Google Search with Python](https://brightdata.co.kr/blog/web-data/scraping-google-with-python)
- **Technical Support:** [Contact Us](mailto:support@brightdata.com)