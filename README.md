# gapi
gapi


````js
/**/

var env={
auth : "acccess_token",
owner: "pinkromeo18",
repo : "gapi",
fileGirls: "girls.txt",
filePhone: "phone.txt",
fileDekin: "dekin.txt"
}
var {auth,owner,repo,fileGirls,filePhone,fileDekin} =env;

var apiGirls=Gapi(auth,owner,repo,fileGirls);
await apiGirls.isget();
await apiGirls.get();
await apiGirls.put(data);

var apiPhone=Gapi(auth,owner,repo,filePhone);
await apiPhone.isget();
await apiPhone.get();
await apiPhone.put(data);

var apiDekin=Gapi(auth,owner,repo,fileDekin);
await apiDekin.isget();
await apiDekin.get();
await apiDekin.put(data);



function base64Decode(text, charset) {
  charset=charset||'utf-8';
  return fetch(`data:text/plain;charset=${charset};base64,` + text)
    .then(response => response.text());
}

function base64Encode(...parts) {
  return new Promise(resolve => {
    const reader = new FileReader();
    reader.onload = () => {
      const offset = reader.result.indexOf(",") + 1;
      resolve(reader.result.slice(offset));
    };
    reader.readAsDataURL(new Blob(parts));
  });
}  

function Gapi(auth,owner,repo,path){
var o={}
const authorization ="token "+auth;
const accept = "application/vnd.github.v3+json"
const content_type = "application/json; charset=utf-8"    
const host = 'https://api.github.com'
const base = `${host}/repos/${owner}/${repo}/`
const file = path||''



o.sha = null /////////

o.isget=async ()=>{
let oldsha = o.sha;
let res = await _get()
o.sha = res.sha
if(oldsha===null||oldsha===undefined) return  true;
return oldsha===o.sha ? false : true;
}

o.get=async ()=>{
  let res = await _get()
  let d=await base64Decode(res.content)
  return d
}
o.put=async (dat)=>{
      var url = base + file
      var method ='PUT'
      var headers = { 
        accept,
        authorization,
        "content-type": content_type
      }
      var sha=o.sha
      var message = ""+Date.now()
      //content
      var content = await base64Encode(dat)

      var body = {
        sha,
        message,
        content,
      }

      if(!body.sha) delete body.sha;
      body =JSON.stringify(body)

      var res = await fetch(url,{method,headers,body})
      .then(d=>d.json())
      .catch(e=>void 0)
      if(!res) return res
      return res
    }    




return Object.assing({},o);

async function _get(){
   var url = base + file
   var method ='GET'
   var headers = { 
     accept,
     authorization
   }
   var body = void 0

   var res = await fetch(url,{method,headers,body,cache:'no-cache'})
   .then(d=>d.json())
   .catch(e=>void 0)
   if(!res) return res
   return res
 }

}

````

















