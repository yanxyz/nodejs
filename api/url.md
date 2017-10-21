# url

有 WHATWG 和 Legacy 两种 API，这里只考虑 WHATWG API

```js
const { URL } = require('url')
import { URL } from 'url'
```

[URL 图解](https://nodejs.org/api/url.html#url_url_strings_and_url_objects)

## URL Constructor


```js
const urlObj = new URL()

Object.getOwnPropertyDescriptors(URL.prototype)
```

urlObj 有这些属性

- .href, 即 url.toString()
- .origin
- .protocol 包含 `:`
- .username
- .password
- .host
- .hostname
- .port
- .pathname 缺省为 `/`
- .search 包含 `?`
- .searchParams
- .hash 包含 `#`

除了 origin，searchParams 只是 getter 之外，其它都是 getter 和 setter。
