<style src="./annotationLayer.css"></style>
<script>
import componentFactory from "./componentFactory.js";
var component = componentFactory({});
if (process) {
  var __process__ = process;
  if (__process__ && __process__.env && __process__.env.VUE_ENV !== "server") {
    if (
      typeof window !== "undefined" &&
      "Worker" in window &&
      navigator.appVersion.indexOf("MSIE 10") === -1
    ) {
      var PDFJS = require("pdfjs-dist/build/pdf.js");
      var PdfjsWorker = require("worker-loader!pdfjs-dist/build/pdf.worker.js");
      PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
    }
    var pdfjsWrapper = require("./pdfjsWrapper.js").default;
    component = componentFactory(pdfjsWrapper(PDFJS));
  }
}

export default component;
</script>