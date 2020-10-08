# makroclickapi
reverse engineer mackroclick to allow scripted ordering

# finding
- API Endpoint : https://ocs-prod-api.makroclick.com/
- Example POST call script when I search for "มรกต"

fetch("https://ocs-prod-api.makroclick.com/next-product/public/api/product/smartSearchV2", {
  "headers": {
    "accept": "application/json, text/plain, */*",
    "accept-language": "en-US,en;q=0.9,th-TH;q=0.8,th;q=0.7,zh-CN;q=0.6,zh;q=0.5",
    "content-type": "application/json;charset=UTF-8",
    "sec-fetch-dest": "empty",
    "sec-fetch-mode": "cors",
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
