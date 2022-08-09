CERAMICNETWORK CRUD OPERATION.
DIDACTICAL PURPOSE.





#part1 code
#create  dir /media/ubuntu/shareddir1/cerami_app_crud2/
D='/media/ubuntu/shareddir1/cerami_app_crud2/'
mkdir $D
cd $D






#installbabel
#es6
#babel
#https://dev.to/geekygeeky/get-started-with-es6-javascript-for-writing-nodejs-using-express-544h

npm i @babel/cli @babel/core @babel/node @babel/preset-env --save-dev
sleep 3
npm i @babel/plugin-proposal-class-properties @babel/plugin-proposal-object-rest-spread --save-dev
sleep 3
npm i rimraf nodemon --save-dev
sleep 3





#DOWNLOAD option1
#DOWNLOAD cerami_app_crud2.ZIP







#DOWNLOAD option2
cd $D
git clone link




now you should have this file hierarchy
/media/ubuntu/shareddir1/cerami_app_crud2
/media/ubuntu/shareddir1/cerami_app_crud2/package.json
/media/ubuntu/shareddir1/cerami_app_crud2/.babelrc
/media/ubuntu/shareddir1/cerami_app_crud2/readme.txt
/media/ubuntu/shareddir1/cerami_app_crud2/src
/media/ubuntu/shareddir1/cerami_app_crud2/src/app.js





#install app
cd $D
npm install





#usage
cd $D
node src/app.js 'help'
node src/app.js 'createdidandceramicauthentication'
node src/app.js 'createandquerydocument'
node src/app.js 'createandupdatedandqueryocument'








part3. extra doc: useful library
#install library
#old
#https://developers.ceramic.network/build/javascript/http/
#https://www.npmjs.com/package/key-did-resolver
#https://www.npmjs.com/package/@ceramicnetwork/3id-did-resolver
#https://npmmirror.com/package/3id-resolver
npm install @ceramicnetwork/http-client
npm install @ceramicnetwork/stream-tile
npm install @ceramicnetwork/3id-did-resolver
//npm install key-did-resolver
npm install did-resolver
npm install 3id-resolver 
npm install dids
npm install @3id/connect
npm install key-did-resolver
npm install @ceramicnetwork/3id-did-resolver 
npm install key-did-provider-ed25519 
 














part3. extra doc: useful links
#/media/ubuntu/shareddir1/cerami_app_crud2/src/
#https://blog.ceramic.network/getting-started-with-ceramic/#things-we-need-to-talk-about
#https://blog.ceramic.network/orbis-launches-web3-social-protocol-on-ceramic-mainnet-and-opens-sdk-to-developers/
#https://developers.ceramic.network/tools/glaze/did-datastore/
#https://developers.ceramic.network/tools/glaze/example/
#https://developers.ceramic.network/build/javascript/quick-start/#__tabbed_1_1
#https://developers.ceramic.network/reference/accounts/key-did/#ed25519

#ceramicnode
#nodeceramic
https://gateway.ceramic.network
https://gateway-clay.ceramic.network
https://ceramic-clay.3boxlabs.com







