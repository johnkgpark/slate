---
title: Rescale RESTful api 

language_tabs:
  - json

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

---

# Introduction

All the API calls need to include the Authorization Token in the HTTP header. 
e.g ```shell -H 'Authorization: Token <API Key>'```

# Analyses

```GET /api/analyses/```

>**Response**  
>```HTTP 200 OK```  
>```Vary: Accept```  
>```Content-Type: application/json```  
>```Allow: GET, HEAD, OPTIONS```  

```json
{
    "count": 46, 
    "previous": null, 
    "results": [
         {
      "code": "adina", 
      "description": "<p><b>A</b>utomatic <b>D</b>ynamic <b>I</b>ncremental <b>N</b>onlinear <b>A</b>nalysis (<b>ADINA</b>) is a finite element analysis (FEA) suite of tools providing a comprehensive FEA solution for modeling structures, fluids, heat transfer, electromagnetics, and multiphysics.</p>", 
      "industries": [
        {
          "icon": "https://d12eutiwfmky5n.cloudfront.net/thumbnails/tools-auto_1.png", 
          "name": "Automotive"
        }, 
        {
          "icon": "https://d12eutiwfmky5n.cloudfront.net/thumbnails/tools-aero_1.png", 
          "name": "Aerospace"
        }
      ], 
      "licenseSettings": [
        {
          "helpText": "The address of the FlexNet license server to use. ([port]@hostname)", 
          "isServer": true, 
          "label": "License", 
          "licenseType": "Sentinel", 
          "name": "LSHOST"
        }
      ], 
      "name": "ADINA", 
      "pricing": "", 
      "resources": [], 
      "thumbnail": "https://d12eutiwfmky5n.cloudfront.net/thumbnails/adina.png", 
      "vendorName": "", 
      "versions": [
        {
          "allowedCoreTypes": [], 
          "eula": null, 
          "mpiCommand": "run-adina -n <mpi-ranks> -t <smp-ranks> -f <input-filename> -p <input-filename-2>", 
          "smpCommand": "run-adina -t <smp-ranks> -f <input-filename> -p <input-filename-2>", 
          "stdCommand": "run-adina -f <input-filename> -p <input-filename-2>", 
          "version": "9.0.0", 
          "versionCode": "9.0.0-openmpi"
        }, 
        {
          "allowedCoreTypes": [], 
          "eula": null, 
          "mpiCommand": "run-adina -n <mpi-ranks> -t <smp-ranks> -f <input-filename> -p <input-filename-2>", 
          "smpCommand": "run-adina -t <smp-ranks> -p1 <input-filename> -p <input-filename-2>", 
          "stdCommand": "run-adina -f <input-filename> -p <input-filename-2>", 
          "version": "9.0.1", 
          "versionCode": "9.0.1-openmpi"
        }
      ]
    }, 
    ...
    ], 
    "next": null
}
```

# Credentials

## Credentials for upload

```POST /api/credentials/```

>**Response**  
>HTTP 201 CREATED  
>Vary: Accept  
>Content-Type: application/json  
>Allow: POST, OPTIONS  

```json
{
    "secretKey": "<AWS Secret Key>", 
    "accessKey": "<AWS Access Key>", 
    "storageDir": "user/user_XXXXX", 
    "expiration": "2014-01-30T03:00:44Z", 
    "sessionToken": "AQoDYXdzEMv//////////wEa0ALhKSZusmhtdW+1dYPIid11chpkA0BpX7W0cAfP9ldAI4uP51/VY9/NxmkIMq9drz9QbtX8/mh7PRxOdTxaYCc1/DddGD3rsRagEwLBFNL5I012zN/sPos7B/pDiOPtNJGzwfg94klXgSZYSGSE4bsLi1pVDm4ay/+eiEQWQluUwCXG0ZDQneKXRg/mxVmSBPwrrqu+c2xkXKZYZ7IXKHv0gLf/g3edNVxKQaoDV2Jo24Ate/gNEz8WSE2A1wp85fAxU8IdTmCxhN4zcem6G8gwmzlyTE5+68gDbFnf7sDnQ9RCi85QDxBGUgZyUGPeE39l2nj9J5qJXvW68YY4ngbqA00SJfEXuBIWOUHoWlOMO/lnA3PDjZXp2ZMVAwpvUshF2YEDew55AknBAVAW04FtfKU/NKtYSVbzcdA3A00YtHLpB436a6bZ8K2HIccS4T4gzOSmlwU="
}
```

## Credentials for particular path(s)

```POST api/credentials/```

>**Data**  
>```{"paths": [{"path": "user/user_BNTMk/SGE/run.sh"}]}```  
>**Headers**  
>```-H 'Content-Type: application/json' -H 'Authorization: Token [API Key]'```  
>**Response**  
>HTTP 201 CREATED  
>Vary: Accept  
>Content-Type: application/json  
>Allow: POST, OPTIONS  

```json
{  
    "secretKey": "<AWS Secret Key>",  
    "accessKey": "<AWS Access Key>",  
    "storageDir": "user/user_XXXXX",  
    "expiration": "2014-01-30T03:19:05Z",  
    "sessionToken": "AQoDYXdzEMv//////////wEa0AI9+fos3N+2Qnyj5jpCqnUu4YQTc9hPoAm4YwMVFzRdSEe0DY7L1xnfDsybpOd3sP20r69jo8T3MCyfofDUGCaIdgRAP6/AQ9J9Z7h8dq0f0fxhIBrRM2neCrpZiFBrbQxtVLWhwGpFF4oyM6AklNy3FemQxs10DSXXZKeMcdS0Ef7BwTFha3d5e4aXbX0kOH4nEk214jGPjUtGiKr48/iSxA4Dk9mm5XMKPUehDKn5aYjiz0y5kVhK1l1Ow3UbPmefe7IhkQtHymZKVJ6wshnAfSAy4KH7NvQyDFDoiNfuOTbuydH6j8Ufs5cSzLJueiKmkvtDac0aVF6/1pLQFpSGRvkA7T1J5qOgTJ/I32iHq2mU4dO2rArb9mbnYxcR58Ur2TNwIibU4arN/3n9/K1DmIDAR0fY1wD6ocfZcNrAhHO+S/lxaCfBHVPH6JGas1Igme2mlwU="  
}  
```
