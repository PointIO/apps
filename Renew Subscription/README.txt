POS New Subscription for V1.3.16 
Setup Notice

TODO list
1. Associate an Intuit keychain to your account (or a SFDC one)
2. Get your QuickBooks companyId and add it to your LIST_OBJECTSMap and CREATEMap as "companyID":"<companyId>"
3. Associate a Docusign keychain to your account
4. Edit the ID of the RELATEDS you want to use from your Docusign Template
5. Edit the MAP entry of your RELATEDS to point to the correct Fact provider
6. Edit the poi_APIdoc_Storage_Location to point to a Folder link of your APIdoc account

How do I do the above?
1. Use the POST /keychain call with a body like:
{
"intuit": {
  "clientId": "<myClientId>",
  "clientSecret": "<myClientSecret>",
  "accessToken": "<myAccessToken>",
  "accessTokenSecret": "<myAccessTokenSecret>"
}}
To get those, go to your QuickBooks dev account: 
https://developer.intuit.com/v2/ui#/app/dashboard -> select one App or create one -> get you development
clientId is Consumer Key and clientSecret is Consumer Secret
Then use those in https://appcenter.intuit.com/Playground/OAuth/IA
To get your accessToken and accessTokenSecret

2. Go to your sandbox repository https://developer.intuit.com/v2/ui#/sandbox
Add a sandbox company or use the CompanyId of an existing one
This is how the AuickBooks fact configuration looks like:
  "LIST_OBJECTSMap": {
    "apidata_method": "GETOBJS",
    "objId": "",
    "objTypeId": "customer",
    "display": "once",
    "companyId": "193514292343952"
  },
  "CREATEMap": {
    "apidata_method": "POST",
    "objId": "",
    "objTypeId": "customer",
    "data": {
      "DisplayName": "$$customername",
      "PrimaryEmailAddr": {
        "Address": "$$customeremail"
      },
      "BillAddr": {
        "Line1": "$$line1",
        "City": "$$city",
        "Country": "$$country",
        "PostalCode": "$$postalcode"
      }
    },
    "display": "never",
    "companyId": "193514292343952"
  }

3. Use the POST /keychain call with a body like:
{"docusign":{"username":"<username>", "password":"<password>"}}

4. Go to your Docusign account templates: https://appdemo.docusign.com/templates/all
Click on the template you want to use
Click the circled i icon next to your template name
Click Copy Id
Go edit your App
Paste the ID in the RELATEDS: "ID":"<template ID>"

5. Import the Template Fact you want to use to your server. 
Grab the Fact id of this Fact
Go edit your App
Paste the id in the RELATEDS: "MAP":"<Fact ID>"

6. Go to /admin
Create a Folder Link
Copy the link
Go edit your App
Paste the link in poi_APIdoc_Storage_Location at the root of the Facts: "poi_APIdoc_Storage_Location":"<myFolderLink>"
WARNING: That will not work on localhost

Here is the Docusign configuration in the App's fact
"READMap": {
    "objId": "$$objId",
    "objTypeId": "Preview",
    "display": "once",
    "skipPreview": true,
    "storagelink": "$$poi_APIdoc_Storage_Location",
    "finishedfilename": "Subscription Agreement Signed.pdf",
    "mode": "demo",
    "apidata_method": "GET",
    "selectedplan": "$$selectedplan",
    "customername": "$$customername",
    "customeraddress": "$$customeraddress"
  },
  "RELATEDS": [
    {
      "ID": "48db3c14-569c-413f-90d3-ae484ac0fbe5",
      "LABEL": "Subscription Agreement",
      "TOOLTIP": "Subscription Agreement",
      "TYPE": "DocusignTemplate",
      "MAP": "571923432d0000c9062ae64f"
    }
  ],
  "poi_APIdoc_Storage_Location": "ecfb2c1e-5a7d-412b-aaad-a2e0d00024ac"