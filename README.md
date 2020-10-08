# makroclickapi
reverse engineer mackroclick to allow scripted ordering

# finding
- API Endpoint : https://ocs-prod-api.makroclick.com/
- Example POST call script when I search for "มรกต"
```javascript
fetch("https://ocs-prod-api.makroclick.com/next-product/public/api/product/smartSearchV2", {
  "headers": {
    "accept": "application/json, text/plain, */*",
    "accept-language": "en-US,en;q=0.9,th-TH;q=0.8,th;q=0.7,zh-CN;q=0.6,zh;q=0.5",
    "content-type": "application/json;charset=UTF-8",
    "sec-fetch-dest": "empty",
    "sec-fetch-site": "same-site"
  },
  "referrer": "https://www.makroclick.com/",
  "referrerPolicy": "strict-origin-when-cross-origin",
  "body": "{\"keyword\":\"มรกต\",\"locale\":\"th_TH\",\"customerType\":\"MKC\",\"assortPriceStoreCode\":\"4\",\"assortOrderStoreCode\":\"4\",\"nonAssortPriceStoreCode\":\"801\",\"nonAssortOrderStoreCode\":\"801\",\"makroNo\":\"00491683180710\",\"includeWeightedFresh\":false}",
  "method": "POST",
  "mode": "cors",
  "credentials": "omit"
})
.then(res => res.json())
.then(console.log)
```
- Create Cart
```javascript
fetch("https://www.makroclick.com/api/createSessionCartOpen", {
  "headers": {
    "accept": "application/json, text/plain, */*",
    "accept-language": "en-US,en;q=0.9,th-TH;q=0.8,th;q=0.7,zh-CN;q=0.6,zh;q=0.5",
    "content-type": "application/json;charset=UTF-8",
    "sec-fetch-dest": "empty",
    "sec-fetch-site": "same-origin"
  },
  "referrer": "https://www.makroclick.com/th/search-results/?keyword=%E0%B8%A1%E0%B8%A3%E0%B8%81%E0%B8%95",
  "referrerPolicy": "strict-origin-when-cross-origin",
  "body": "{\"openCartPopOver\":false}",
  "method": "POST",
  "mode": "cors",
  "credentials": "include"
})
.then(res => res.json())
.then(console.log)
```
- Add item to cart
```javascript
fetch("https://ocs-prod-api.makroclick.com/next-ocs-member/user/cart/changeQuantity", {
  "headers": {
    "accept": "application/json, text/plain, */*",
    "accept-language": "en-US,en;q=0.9,th-TH;q=0.8,th;q=0.7,zh-CN;q=0.6,zh;q=0.5",
    "authorization": "Bearer 966b9114-8dfe-4970-8197-edf9d6fa2a95",
    "content-type": "application/json;charset=UTF-8",
    "sec-fetch-dest": "empty",
    "sec-fetch-site": "same-site"
  },
  "referrer": "https://www.makroclick.com/",
  "referrerPolicy": "strict-origin-when-cross-origin",
  "body": "{\"locale\":\"th_TH\",\"productCode\":\"312130\",\"quantity\":2,\"add\":true}",
  "method": "POST",
  "mode": "cors",
  "credentials": "include"
})
.then(res => res.json())
.then(console.log)
```
- Remove Item from cart
```javascript
fetch("https://ocs-prod-api.makroclick.com/next-ocs-member/user/cart/removeItem", {
  "headers": {
    "accept": "application/json, text/plain, */*",
    "accept-language": "en-US,en;q=0.9,th-TH;q=0.8,th;q=0.7,zh-CN;q=0.6,zh;q=0.5",
    "authorization": "Bearer 966b9114-8dfe-4970-8197-edf9d6fa2a95",
    "content-type": "multipart/form-data; boundary=----WebKitFormBoundaryLfuwLL9WW2SxNSDX",
    "sec-fetch-dest": "empty",
    "sec-fetch-site": "same-site"
  },
  "referrer": "https://www.makroclick.com/",
  "referrerPolicy": "strict-origin-when-cross-origin",
  "body": "------WebKitFormBoundaryLfuwLL9WW2SxNSDX\r\nContent-Disposition: form-data; name=\"productCode\"\r\n\r\n683111\r\n------WebKitFormBoundaryLfuwLL9WW2SxNSDX\r\nContent-Disposition: form-data; name=\"locale\"\r\n\r\nth_TH\r\n------WebKitFormBoundaryLfuwLL9WW2SxNSDX--\r\n",
  "method": "POST",
  "mode": "cors",
  "credentials": "include"
})
.then(res => res.json())
.then(console.log)
```
