# sinon-express-mock

Simple request and response mock objects to pass into Express routes when testing using Sinon.

The mock objects attach Sinon spys to request methods. See `src/index.js` for a full list of stubbed out methods.

## Install

```shell
npm install --save-dev sinon-express-mock
```

Depends on:

- Node v4+ (or `Object.assign` support needed)
- Sinon

## Usage

Contents of `src/foo.js`:

```js
export default (req, res) => {
  res.json({ foo: req.body.foo })
}
```

Contents of `test/foo-test.js`:

```js
import route from '../src/foo'
import { expect } from 'chai'
import { mockReq, mockRes } from 'sinon-express-mock'

describe('my route', () => {
  it('should foo the bar', () => {

    const request = {
      body: {
        foo: 'bar',
      },
    }
    const req = mockReq(request)
    const res = mockRes()

    route(req, res)

    expect(res.json).to.be.calledWith({ foo: request.body.foo })
  })
})
```

## Changelog

### V2.0.0

- Upgraded from
  - babel-cli: 6.2.0 → ^6.26.0
  - babel-preset-es2015: 6.1.18 → babel-preset-env: ^1.6.1
  - sinon: 1.17.2 → ^4.1.3

### v1.3.1

- Bundle fix from #3

### pre v1.3.1

- Changelog didn't exist! 😱

## Credits

Dana Woodman and [contributors](https://github.com/danawoodman/sinon-express-mock/graphs/contributors)

## License

MIT
