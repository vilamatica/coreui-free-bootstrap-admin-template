HOWTO
======

* First of all, execute `npm run install`:
* Modify scss/_cutom.css and scss/_variables.css
* To take a look, execute `npm run dev`
* Icons are buggy, so it's necessary install clone https://github.com/coreui/coreui-icons
* To merge into SGT:

``` 
export SGT_SRC_WORKING_DIR="/path/to/sgt/src";
export COREUI_ICONS="/path/to/coreui-icons";
export COREUI_SRC="/path/to/coreui";

cd "${COREUI_SRC}";
npm run build-clean
npm run build
cp ./node_modules/@coreui/chartjs/dist/js/coreui-chartjs.bundle.js.map ./dist/vendors/@coreui/chartjs/js/
cp ./node_modules/@coreui/chartjs/dist/css/coreui-chartjs.css.map ./dist/vendors/@coreui/chartjs/css/
cp ./node_modules/@coreui/coreui/dist/js/coreui.bundle.min.js.map ./dist/vendors/@coreui/coreui/js/
cp ./node_modules/@coreui/icons/css/brand.css.map dist/vendors/@coreui/icons/css
cp ./node_modules/@coreui/icons/css/brand.min.css.map dist/vendors/@coreui/icons/css
cp ./node_modules/@coreui/icons/css/flag.css.map dist/vendors/@coreui/icons/css
cp ./node_modules/@coreui/icons/css/flag.min.css.map dist/vendors/@coreui/icons/css
cp ./node_modules/@coreui/icons/css/free.css.map dist/vendors/@coreui/icons/css
cp ./node_modules/@coreui/icons/css/free.min.css.map dist/vendors/@coreui/icons/css
rm -rf dist/vendors/@coreui/icons
mkdir -p dist/vendors/@coreui/icons
cp -a ${COREUI_ICONS}/css dist/vendors/@coreui/icons
cp -a ${COREUI_ICONS}/fonts dist/vendors/@coreui/icons
cp -a ${COREUI_ICONS}/js dist/vendors/@coreui/icons
cp -a ${COREUI_ICONS}/svg dist/vendors/@coreui/icons
cp -a ${COREUI_ICONS}/sprites/brand.svg dist/vendors/@coreui/icons/svg/
cp -a ${COREUI_ICONS}/sprites/flag.svg dist/vendors/@coreui/icons/svg/
cp -a ${COREUI_ICONS}/sprites/free.svg dist/vendors/@coreui/icons/svg/

rm -rf ${SGT_SRC_WORKING_DIR}/portal/static/coreui/css/
rm -rf ${SGT_SRC_WORKING_DIR}/portal/static/coreui/js/
rm -rf ${SGT_SRC_WORKING_DIR}/portal/static/coreui/vendors/
cp -a dist/css/ dist/js/ dist/vendors/ ${SGT_SRC_WORKING_DIR}/portal/static/coreui
```
