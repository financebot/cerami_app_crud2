//file random id 23984573209845723457


//see documantation at the end of this file
//reade the file readme too.

//imports
import { CeramicClient } from '@ceramicnetwork/http-client'
import { DID } from 'dids'
import { getResolver as getKeyResolver } from 'key-did-resolver'
import { getResolver as get3IDResolver } from '@ceramicnetwork/3id-did-resolver'
import { TileDocument } from '@ceramicnetwork/stream-tile'
import { Ed25519Provider } from 'key-did-provider-ed25519'
import { TileLoader } from '@glazed/tile-loader'







//PART1. MANAGE ARGUMENTS ETC
//print arguments
//console.log('args: ', process.argv);
//console.log('args: ', process.argv.slice(2));


// 

//define accepted argument. [start]
//This section has nothing to do with ceramic, web3, etc
let accepted_argument=['createdidandceramicauthentication', 'createandquerydocument', 'createandupdatedandqueryocument',]





async function is_x_inthe_collection(x,collection) 
{

	for (const element of collection) 
	{ 
		
		if(element==x) { return true}
	}
	
	return false		
	
}





let x_is_inthe_collection=await is_x_inthe_collection(process.argv[2],accepted_argument)
	
	
if(process.argv[2]=='help' || process.argv[2]=='' || process.argv[2]==null || process.argv[2]==undefined  || x_is_inthe_collection==false)
{
 console.log(`
	 
Usage.
cd /media/ubuntu/shareddir1/cerami_app_crud2
node src/app.js 'help'
node src/app.js 'createdidandceramicauthentication'
node src/app.js 'createandquerydocument'
node src/app.js 'createandupdatedandqueryocument'

`	 
)
}











//sleep function
function sleep(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}




//define accepted argument. [end]








//part2. DEFINE GLOBAL VARIABLE 


//set url node
//const API_URL = 'https://gateway-clay.ceramic.network'
//const API_URL = 'https://gateway.ceramic.network'
const API_URL = 'https://ceramic-clay.3boxlabs.com'


// Connect to a Ceramic node
const ceramic_client_0 = new CeramicClient(API_URL)
//console.log('ceramic_client_0: ', ceramic_client_0)	
//console.log('\n\n')	




//create document contents
var content1={ title: 'document45454', message: 'message6476575' }  
var content2={ title: 'document45454', message: 'message969696' }  






//create seed for authentication ed25519
const seed_0 = await new Uint8Array(32) //  32 bytes with high entropy
//console.log('seed_0: ', seed_0)	
//console.log('\n\n')	













//part3. 
//define function to manage 3id, stream, etc 

 
 
 
 //define function authenticateCeramic()
 // `seed` must be a 32-byte long Uint8Array
 async function authenticateCeramic(seed) 
 {
	
 const provider = await new Ed25519Provider(seed)
 
 const did = await  new DID({ provider, resolver: getKeyResolver() })
 // Authenticate the DID with the provider
 await did.authenticate()
 // The Ceramic client can create and update streams using the authenticated DID
 ceramic_client_0.did = did
 await console.log('ceramic_client_0.did= ', ceramic_client_0.did);		
 await console.log('\n\n');		
 
 }

 
 
 
 


 
 //define function createdocument() 
 async function createdocument(ceramic_client, content, seed) 
 {
	 
	 
 //authentication	 
 await authenticateCeramic(seed)  
 await console.log('ceramic_client= ', ceramic_client);		
 await console.log('content= ', content);		
	 
	 
  //create document	 
  // The following call will fail if the Ceramic instance does not have an authenticated DID
  const doc = await TileDocument.create(ceramic_client, content)
  
  
  // The stream ID of the created document can then be accessed as the `id` property
  await console.log('\n\n\n\n\n');		  
  await console.log('doc.43534= ', doc);		  
  await console.log('\n\n\n\n\n');		  
  console.log('doc.id.6565= ', doc.id);		  
  await console.log('\n\n\n\n\n');		  
  
  
  return doc.id
 }
 
 
 
 
 






 //define function
 // The `id` argument can be a stream ID (to load the latest version)
 // or a commit ID (to load a specific version)
 async function loaddocumenttile(ceramic_client, id) 
 {
  let result= await TileDocument.load(ceramic_client, id)
  
  //await console.log(result) 
  await console.log(result.content) 
  
  return result
  
  
 }



 
 
 
 
 
 
 
 
 
 

 
 
 
 
 
 
 
 //define function updatedocument() 
 async function updatedocument(ceramic_client, content, seed, streamId) 
 {
	 
 await authenticateCeramic(seed)  
 //await console.log('ceramic_client_0= ', ceramic_client_0);		
 //await console.log('content= ', content);		
	 



  // First, we need to load the document
  const doc = await TileDocument.load(ceramic_client_0, streamId)
  
  

  // The following call will fail if the Ceramic instance does not have an authenticated DID
  await doc.update(content)
  await console.log('\n\n');		  
  await console.log('doc= ', doc.content);		  
  await console.log('\n\n\n');		  
  
  return doc.id
 }
 
 
 
 

 
 
 
 
 //define function createandupdatedandqueryocument() 
 async function createandupdatedandqueryocument(ceramic_client, content1, content2, seed) 
 {
 
 
 
 
 //call function createdocument()
 var streamId1=await createdocument(ceramic_client, content1, seed)  


 //call function TileDocument.load()
 let doc_old= await TileDocument.load(ceramic_client, streamId1)
 let doc_old_content=doc_old.content
 let doc_old_id=doc_old.id
 await console.log('wait...') 
 await sleep(2000)
 await console.log('\n\n\n')
 
 
 //call function updatedocument()
 var streamId2=await updatedocument(ceramic_client, content2, seed, streamId1)  

 //call function TileDocument.load()
 let doc_new= await TileDocument.load(ceramic_client, streamId2)
 let doc_new_content=doc_new.content
 let doc_new_id=doc_new.id
 
 
 
 await console.log('\n\n\n') 
 await console.log('Final docs') 
 await console.log('doc_old.content: ', doc_old_content) 
 await console.log('doc_old_id.id: ', doc_old_id) 
 await console.log('\n\n\n') 
 await console.log('doc_new.content: ', doc_new_content) 
 await console.log('doc_new_id.id: ', doc_new_id) 
 await console.log('\n\n\n') 
 
 
 } 
 
 
 
 
 
 

 
 
 
 
 
 
 
 
 
 //define function createandupdatedandqueryocument() 
 async function createandquerydocument(ceramic_client, content, seed) 
 {
 
 
 
 
 //call function createdocument()
 var streamId=await createdocument(ceramic_client, content, seed)  



 //call function
 //example. streamId ='k3y52l7qbv1fry5xdn5336sz63r8yfy2yjsytjdb4kvo4cmhobniboxi7stmanhmo'
 await loaddocumenttile(ceramic_client, streamId)
 
 
 
 } 
 
 
 
 
 
 
 
 
 
 
 
///////////////////////////////////////////////////////////////////////
//part4. call functions











//scenario createdidandceramicauthentication
if(process.argv[2]=='createdidandceramicauthentication')
{
 console.log('scenario createdidandceramicauthentication');		





 //call function
 authenticateCeramic(seed_0)
}





























//scenario createandquerydocument
if(process.argv[2]=='createandquerydocument')
{
 console.log('scenario createandquerydocument');		

 


 

 //call function createandupdatedandqueryocument()
 createandquerydocument(ceramic_client_0, content1, seed_0) 
 
}

















//scenario createandupdatedandqueryocument
if(process.argv[2]=='createandupdatedandqueryocument')
{
 console.log('scenario createandupdatedandqueryocument');		

 


 

 //call function createandupdatedandqueryocument()
 createandupdatedandqueryocument(ceramic_client_0, content1, content2, seed_0) 
 
}


















//documantation


/*

doc1. useful links
node1=https://gateway.ceramic.network
node2=https://gateway-clay.ceramic.network
node3=https://ceramic-clay.3boxlabs.com
/root/.npm-global/lib/node_modules/@ceramicnetwork/cli/node_modules/@ceramicnetwork/3id-did-resolver
https://developers.ceramic.network/build/javascript/http/
https://developers.ceramic.network/build/javascript/authentication/
https://developers.ceramic.network/reference/accounts/3id-did/#3id-did-resolver
https://developers.ceramic.network/docs/advanced/standards/stream-programs/
https://developers.ceramic.network/reference/stream-programs/tile-document/

search: How to generate deterministic keypairs using ed25519
https://ethereum.stackexchange.com/questions/48437/how-to-generate-deterministic-keypairs-using-ed25519
https://github.com/ceramicnetwork/key-did-provider-ed25519
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Uint8Array/Uint8Array

https://developers.ceramic.network/reference/glaze/modules/tile_loader/


//create datamodel etc
https://developers.ceramic.network/tools/glaze/example/#__tabbed_2_1



//did_key
https://w3c-ccg.github.io/did-method-key/
*/






/*
doc2. useful libraries
#install library
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
*/








/*
doc3. Usage.
cd /media/ubuntu/shareddir1/ceramic_http_client
node src/app.js 'loaddocument'
node src/app.js 'help'
node src/app.js 'createdid'



*/






