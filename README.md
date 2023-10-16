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

function Gapi(auth,owner,repo,path){
var o={}
const authorization ="token "+auth;
const accept = "application/vnd.github.v3+json"
const content_type = "application/json; charset=utf-8"    
const host = 'https://api.github.com'
const base = `${host}/repos/${owner}/${repo}/`
const file = path||''


o.sha = null /////////

o.isget=async ()=>{}
o.get=async ()=>{}
o.put=async ()=>{}

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

















