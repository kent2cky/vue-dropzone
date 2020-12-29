# vue-dropzone

**Modified**
This codebase was forked from the open source vue-dropzone and modified
to suit my specific use on my project "CatalogNg". I modified the underlying dropzone.js codes to make it send files without appending and sending them in a formData object.

This suits my use case because my cloud storage a BackBlaze expects to store raw files and not having to extract them from a formData.

**What Did I Modify**
I went to the source code of Dropzone.js located at `node_modules/dropzone/dist/dropzone.js` and modified the submitRequest function to
`
key: "submitRequest",
value: function submitRequest(xhr, formData, files) {
// extract file from formData before send
// because the transformed files are appended to formData
const formFile = formData.get('file');
xhr.send(formFile);
//xhr.send(formData); // this is the official implementation
} // Called internally when processing is finished.
// Individual callbacks have to be called in the appropriate sections.

},

`

More details can be fount if you run `git log -p` or runni command.

**CO-MAINTAINERS WANTED**
This component has far outgrown my initial expectations and I'm not able to provide the amount of support that users require. If you'd like to help out with it's maintenance drop a [note on this issue](https://github.com/rowanwins/vue-dropzone/issues/473)

A Vue component for file uploads, powered by [Dropzone.js](http://www.dropzonejs.com/). [Check out the demo](https://rowanwins.github.io/vue-dropzone/docs/dist/index.html).

A **Nuxt SSR-compatible** component can be found at [npm](https://www.npmjs.com/package/nuxt-dropzone) and [github](https://github.com/Etheryte/nuxt-dropzone). Thanks to [@Etheryte](https://github.com/Etheryte)

---

![](https://i.imgur.com/kUbjks1.gif)

## Development

```bash
# install your dependencies
npm install

# install vue-dropzone
npm install vue2-dropzone

(or with yarn)

yarn add vue2-dropzone

# Execute dependencies script
npm run dev

# serve example and docs at localhost:8080
npm run start

# build any changes made
npm run build
```
