import groovy.json.JsonOutput 

node {

    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Restore') {

        sh 'dotnet restore'
    }

    stage('Build') {
	
	sh 'dotnet build'

    }

    stage('Publish') {
    
	sh 'dotnet publish'

    }

    stage('Zip') {

	sh 'zip -r /tmp/test.zip demo-dotnet-webapp/bin/Debug/netcoreapp2.0/publish'

    }

    stage('Provision Dev App') {
        /*
         *
         *  */

        withCredentials([string(credentialsId: 'demo-morph-scrt', variable: 'bearer')]) {
            String morpheusUrl = 'https://demo.morpheusdata.com/api/apps'

            Map<?, ?> postBody = [
  "image": "/assets/apps/template.png",
  "tiers": [
    "Web": [
      "linkedTiers": [
        "Database"
      ],
      "tier": [
        "bootOrder": 1,
        "lockedFields": [
          "bootOrder"
        ]
      ],
      "instances": [
        [
          "instance": [
            "type": "customiis",
            "cloud": "VMware vCenter",
            "layout": [
              "code": "d881d9e2-bb74-4fe4-898c-54f5e2e16b54",
              "id": 948
            ],
            "expireDays": "2",
            "configEnabled": false,
            "name": "frontending",
            "allowExisting": false,
            "shutdownDays": "1",
            "userGroup": [
              "id": ""
            ],
            "networkDomain": [
              "id": 27
            ]
          ],
          "servicePlanOptions": [
            "maxCores": 2,
            "coresPerSocket": 1
          ],
          "backup": [
            "backupRepository": 1,
            "createBackup": true,
            "jobAction": "new",
            "jobRetentionCount": "2",
            "providerBackupType": "null",
            "enabled": true,
            "showScheduledBackupWarning": false
          ],
          "networkInterfaces": [
            [
              "ipMode": "dhcp",
              "primaryInterface": true,
              "showNetworkPoolLabel": false,
              "showNetworkDhcpLabel": true,
              "network": [
                "idName": "VM Network",
                "pool": [
                  "id": 2,
                  "name": "10.30.20.0/22"
                ],
                "id": "network-1",
                "hasPool": true
              ],
              "networkInterfaceTypeId": 4,
              "networkInterfaceTypeIdName": "VMXNET 3"
            ]
          ],
          "volumes": [
            [
              "vId": 512080,
              "controllerMountPoint": "2029354:0:5:0",
              "size": 40,
              "maxIOPS": null,
              "name": "root",
              "rootVolume": true,
              "storageType": 1,
              "datastoreId": "auto",
              "maxStorage": 0
            ]
          ],
          "storageControllers": [
            [
              "removable": false,
              "editable": false,
              "name": "IDE 0",
              "typeName": "IDE",
              "maxDevices": 2,
              "displayOrder": 0,
              "active": true,
              "unitNumber": "null",
              "typeId": 2,
              "id": 2029352,
              "category": "ide",
              "busNumber": "0"
            ],
            [
              "removable": false,
              "editable": false,
              "name": "SCSI controller 0",
              "typeName": "SCSI LSI Logic SAS",
              "maxDevices": 15,
              "displayOrder": 1,
              "active": true,
              "unitNumber": "3",
              "typeId": 5,
              "id": 2029354,
              "category": "scsi",
              "busNumber": "0"
            ],
            [
              "removable": false,
              "editable": false,
              "name": "IDE 1",
              "typeName": "IDE",
              "maxDevices": 2,
              "displayOrder": 2,
              "active": true,
              "unitNumber": "null",
              "typeId": 2,
              "id": 2029353,
              "category": "ide",
              "busNumber": "1"
            ]
          ],
          "lock": [
            "servicePlanOptions": [
              "maxCores": false
            ]
          ],
          "config": [
            "resourcePoolId": "resgroup-3248",
            "createUser": true,
            "vmwareFolderId": "group-v29287"
          ],
          "plan": [
            "code": "vm-4096",
            "id": 148
          ],
          "lockedFields": [],
          "ports": [
            [
              "name": "",
              "port": "",
              "lb": ""
            ]
          ],
          "metadata": [
            [
              "name": "",
              "value": ""
            ]
          ],
          "evars": [
            [
              "name": "",
              "value": ""
            ]
          ]
        ]
      ]
    ],
    "Database": [
      "linkedTiers": [],
      "instances": [
        [
          "instance": [
            "type": "sql_serv",
            "cloud": "VMware vCenter",
            "layout": [
              "code": "87c453c3-a41b-475d-8038-cac6866bd1cf",
              "id": 847
            ],
            "expireDays": "2",
            "configEnabled": false,
            "name": "backending",
            "allowExisting": true,
            "shutdownDays": "1",
            "userGroup": [
              "id": ""
            ],
            "networkDomain": [
              "id": 27
            ]
          ],
          "servicePlanOptions": [
            "maxCores": 2,
            "coresPerSocket": 1
          ],
          "backup": [
            "backupRepository": 1,
            "createBackup": true,
            "jobAction": "new",
            "jobRetentionCount": "2",
            "providerBackupType": -1,
            "enabled": true,
            "showScheduledBackupWarning": false
          ],
          "networkInterfaces": [
            [
              "ipMode": "dhcp",
              "primaryInterface": true,
              "showNetworkPoolLabel": false,
              "showNetworkDhcpLabel": true,
              "network": [
                "idName": "VM Network",
                "pool": [
                  "id": 2,
                  "name": "10.30.20.0/22"
                ],
                "id": "network-1",
                "hasPool": true
              ],
              "networkInterfaceTypeId": 4,
              "networkInterfaceTypeIdName": "VMXNET 3"
            ]
          ],
          "volumes": [
            [
              "vId": 512080,
              "controllerMountPoint": "2029354:0:5:0",
              "size": 40,
              "maxIOPS": null,
              "name": "root",
              "rootVolume": true,
              "storageType": 1,
              "datastoreId": "auto",
              "maxStorage": 0
            ]
          ],
          "storageControllers": [
            [
              "removable": false,
              "editable": false,
              "name": "SCSI controller 0",
              "typeName": "SCSI LSI Logic SAS",
              "maxDevices": 15,
              "displayOrder": 0,
              "active": true,
              "unitNumber": "3",
              "typeId": 5,
              "id": 2029354,
              "category": "scsi",
              "busNumber": "0"
            ],
            [
              "removable": false,
              "editable": false,
              "name": "IDE 1",
              "typeName": "IDE",
              "maxDevices": 2,
              "displayOrder": 1,
              "active": true,
              "unitNumber": "null",
              "typeId": 2,
              "id": 2029353,
              "category": "ide",
              "busNumber": "1"
            ],
            [
              "removable": false,
              "editable": false,
              "name": "IDE 0",
              "typeName": "IDE",
              "maxDevices": 2,
              "displayOrder": 2,
              "active": true,
              "unitNumber": "null",
              "typeId": 2,
              "id": 2029352,
              "category": "ide",
              "busNumber": "0"
            ]
          ],
          "config": [
            "resourcePoolId": "resgroup-3248",
            "createUser": true,
            "vmwareFolderId": "group-v29287"
          ],
          "plan": [
            "code": "vm-4096",
            "id": 148
          ],
          "ports": [
            [
              "name": "",
              "port": "",
              "lb": ""
            ]
          ],
          "metadata": [
            [
              "name": "",
              "value": ""
            ]
          ],
          "evars": [
            [
              "name": "",
              "value": ""
            ]
          ]
        ]
      ]
    ]
  ],
  "name": "example1",
  "templateImage": "",
  "type": "morpheus",
  "id": 162,
  "templateName": "Windows WebApp",
  "group": [
    "id": 21,
    "name": "Adam"
  ],
  "environment": "Dev"
]
 
           echo morpheusApp.buildApp(morpheusUrl, postBody, "${bearer}")
        }
    }


}
