node-sass Docker Image
===

Docker Image based on `node:strech-slim` with node-sass support. Additionally this
image also includes:

* fontcustom
* sfnt2woff
* fontforge

### Usage

This container comes with a globally installed gulp-sass package. To speedup
things you can use `npm link` to link the package to the local `node_modules`
folder prior to `npm install`.

Use this image using `docker run`:

```bash
docker run --rm --volumes-from davshopbase_web_1 \
  remuslazar/docker-node-sass:node6-sass2.2.0 /bin/sh -c \
  "cd /data/www-provisioned/Packages/Sites/CRON.DavShop/Layout ; \
   mkdir -p node_modules ; \
   [ -d node_modules/gulp-sass ] || npm link gulp-sass ; \
   npm install ; bower install -s -f --allow-root ; gulp --neos"
```

### node-sass Versions

Currently there are various image tags matching the node-sass versions:

* node6-sass2.2.0: with gulp-sass 2.2.0
* node6-sass3.1.0: with gulp-sass 3.1.0

E.g. to use `node-sass`@`node6-sass2.2.0` use `remuslazar/docker-node-sass:node6-sass2.2.0`

### Development

See `Makefile` on how to build the images.

### Author

Remus Lazar
