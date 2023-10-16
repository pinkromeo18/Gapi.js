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
 o.env={}
 o.env.auth =auth;
 o.env.owner =owner;
 o.env.repo =repo;
 o.env.path =path;
 o.env.sha = null;

 o.isget=async ()=>{}
 o.get=async ()=>{}
 o.put=async ()=>{}

 return Object.assing({},o);
}

````
