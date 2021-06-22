# Running the simulator

With the Docker containers running and required objects and entities created, we are now ready to start the simulation. The workflow shall consist of the following steps:

1. Checking that all created entities are present in the ORION context broker.
2. Creating a simulated work order and checking that it correctly enters the system.
3. When the scheduled time for the work order arrives, checking that the robot simulator begins "moving" and correctly communicates this to the rest of the system.
4. Let the work order be completed and check that this is correctly translated to the system.

## Initial check

Firstly, we will check that all entities created in the previous step are present in the ORION context broker. For this, we use Postman with the previously imported collection.

1. Go to `orion > entities` and select `get entities by type`
2. In the "Params" section of the request, check "type=AMR"
3. Send the request
4. The response should be a "200 OK" with the following data (`...` represents the details of each attribute -- too long to place here):
```json
[
    {
        "id": "urn:ngsi-ld:AMR:aabbccddeeff",
        "type": "AMR",
        "action": {...},
        "available": {...},
        "battery": {...},
        "connectivity": {...},
        "dateCreated": {...},
        "dateModified": {...},
        "heartbeat": {...},
        "location": {...},
        "name": {...},
        "pendingDestination": {...},
        "refDestination": {...},
        "refPayload": {...},
        "refWorkOrder": {...},
        "status": {...},
        "version": {...}
        
    }
]
```
5. Next we will check the warehouse, using the same request but with different parameters
6. In the "Params" section of the request, check "type=Warehouse"
7. Send the request
8. The response should be a "200 OK" with the following data (`...` represents the details of each attribute -- too long to place here):
```json
[
    {
        "id": "urn:ngsi-ld:Warehouse:ba0a43d899b744cf9f11619258401e46",
        "type": "Warehouse",
        "dateCreated": {...},
        "dateModified": {...},
        "erpId": {...},
        "location": {...},
        "name": {...},
        "status": {...}
    }
]
```
9. Next we will check the idle station, using the same request but with different parameters
10. In the "Params" section of the request, check "type=Idlestation"
11. Send the request
12. The response should be a "200 OK" with the following data (`...` represents the details of each attribute -- too long to place here)
```json
[
    {
        "id": "urn:ngsi-ld:Idlestation:e8473aa880ff4107a763aa528bba7959",
        "type": "Idlestation",
        "dateCreated": {...},
        "dateModified": {...},
        "location": {...},
        "name": {...},
        "refRobot": {...},
        "status": {...}
    }
]
```
13. Finally we will check the work stations, using the same request but with different parameters
14. In the "Params" section of the request, check "type=Workstation"
15. Send the request
16. The response should be a "200 OK" with the following data (`...` represents the details of each attribute -- too long to place here)
```json
[
    {
        "id": "urn:ngsi-ld:Workstation:5d1794f1448c4791ac66860890e92723",
        "type": "Workstation",
        "dateCreated": {...},
        "dateModified": {...},
        "erpId": {...},
        "location": {...},
        "name": {...},
        "status": {...}
    },
    {
        "id": "urn:ngsi-ld:Workstation:aeff3cb499de4ec5b56d80bf61977759",
        "type": "Workstation",
        "dateCreated": {...},
        "dateModified": {...},
        "erpId": {...},
        "location": {...},
        "name": {...},
        "status": {...}
    }
]
```
**Note:** *there are two workstations due to the previous step where we created two entities with this type.*

## Creating a work order



## Checking work order execution



## Final check

