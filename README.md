# superagent-use

Global plugin support for [SuperAgent](https://github.com/visionmedia/superagent/).

## Summary

Instead of manually calling `use()` for every request, `use()` is called automatically for every request.

## Example

```js
/* The superagent-use module returns a clone of the superagent provided with the new functionality. */
var agent = require('superagent-use')(require('superagent'));
var prefix = require('superagent-prefix'); /* A sample superagent plugin/middleware. */

agent.use(prefix('https://api.example.com'));

agent
  .post('/auth')
  .send({user: 'foo', pass: 'bar123'})
  .on('request', function(req) {
    console.log(req.url); // => https://api.example.com/auth
  })
  .end(function(err, res) {
    //
  });
```
