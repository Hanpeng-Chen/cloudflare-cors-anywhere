# cloudflare-cors-anywhere
Cloudflare CORS proxy in a worker.

CLOUDFLARE-CORS-ANYWHERE

Source:
https://github.com/Zibri/cloudflare-cors-anywhere

Demo:
https://bold-forest-51f4.hanpengchen.workers.dev

Reference Article:
https://www.chenhanpeng.com/create-own-cors-anywhere-to-resolve-the-request-with-403

Deploy workers:
https://workers.cloudflare.com/

Example:
```javascript
fetch('https://bold-forest-51f4.hanpengchen.workers.dev/?https://httpbin.org/post', {
  method: 'post',
  headers: {
    'x-foo': 'bar',
    'x-bar': 'foo',
    'x-cors-headers': JSON.stringify({
      // allows to send forbidden headers
      // https://developer.mozilla.org/en-US/docs/Glossary/Forbidden_header_name
      'cookies': 'x=123'
    }) 
  }
}).then(res => {
  // allows to read all headers (even forbidden headers like set-cookies)
  const headers = JSON.parse(res.headers.get('cors-received-headers'))
  console.log(headers)
  return res.json()
}).then(console.log)
```

Note:

All received headers are also returned in "cors-received-headers" header.

Note about the DEMO url:

Abuse (other than testing) of the demo will result in a ban.  
The demo accepts only fetch and xmlhttprequest.  

To create your own is very easy, you just need to set up a cloudflare account and upload the worker code.  

My personal thanks to Damien Collis for his generous and unique donation.    

