# apps

Publicly available App exports to be imported in your pointflow server.
As this repository is public, make sure that no private credentials or sensible information is present in your Apps.

The folders that contain the Apps are the following:
* frontYard: Everything is the front yard is available to the world to see and goes on the demoflow03 server instance
* livingRoom: Put here Apps that you are ready to show to your friends but that would make you blush if shared publicly
* toolShed: Put there Apps that are used to debug you other Appsa

* basement: This is for all your Apps that are on ongoing development, and somewhere to back them up 
* kitchen: For all Apps that are experiments, perfect r\folder if your App will not work on current servers for a lack of the right asset
* theCorner: App that used to work but are now broken go in the corner until they are ready to behave

The server version used to develop the apps in the frontYard, livingRoom and toolShed must be specified in this readme, to be sure they can still run on the la server releease.


* frontYard
    - Contract Negociation for v1.3.4
    - Wire Transfer for v1.3.4 + PointIOWireTransfer fields map
    - Event App for v1.3.4
	- Add SFDC Contracts	
	- Admin - processesReset 	v1.2.27
	- Docusign APIdoc Contract Negotiation 	v1.2.27
	- IT helpdesk Scheduler Demo 	v1.2.27
	- Kobil Demo Transaction Approval 	v1.2.27
	- Meter Reading 	v1.2.27
	- Oauth Connector 	v1.2.27
	- Oppty Approval 	v1.2.27
	- SFT Request 	v1.2.27
	- Time Entry v1.2.24
	- Customized Time Entry v1.2.24

* livingRoom
	- Create New Graphical Project 		v1.2.27
	- Email Campaign	v1.2.27
	- Event App 	v1.2.27
	- Review Graphical Projects 	v1.2.27
	- Twitter Connector 	v1.2.27
	- Update Graphical Project 		v1.2.27
	- User Profile  v.1.2.28
		* NOTES: + User Profile Records must be loaded in mongo: mongoimport --db pointflow --collection objectstore --file "/Users/Tim/Documents/dossierrecords.json"
	- Checkin Key Set v1.2.30a
	- Checkout Key Set v1.2.30a


* toolShed
	- Autoform & Test Facts inspired by Comcast User Profile 		v1.2.27

Known breaking changes for Apps in server version
	- v1.2.24 Is running on Java 8
	- v1.2.26 Revision to JSON format of Apps, Forms, Facts structures (see evolution script to upgrade)