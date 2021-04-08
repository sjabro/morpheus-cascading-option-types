# Cascading Option Lists Configurations

To create cascading option lists, there are a few considerations. The option types must be set to validate based on previsou selections, and you need to ensure proper translation of the returns.

In this walk through, we will be creating an Option List and then its Option Type in turn. You could just make all the lists and then the types if you want.

## Groups

### Option List Configuration

| Name        	| Groups                  	|
|-------------	|-------------------------	|
| Description 	| Get all Morpheus Groups 	|
| Type        	| Morpheus API            	|
| Visibility  	| You Choose              	|
| Option List 	| Groups                  	|

Translatiopn Script
```javascript
//Grab All Groups and Push Values

for (var x = 0; x < data.length; x++) {
results.push({name:data[x].name, value:data[x].id});
    }
```
Request Script
```javascript 

```

### Option Type Configuration

| Name                     	| Selected Group             	|
|--------------------------	|----------------------------	|
| Description              	| Group Selected by the User 	|
| Field Name               	| selectedGroup              	|
| Export As Tag            	| You Choose                 	|
| Dependent Field          	|                            	|
| Visibility Field         	|                            	|
| Display Value on Details 	|                            	|
| Type                     	| Select List                	|
| Label                    	| Group                      	|
| Default Value            	|                            	|
| Help Block               	|                            	|
| Required                 	| Yes                        	|
| Option List              	| Groups                     	|

## Clouds

### Option List Configuration

| Name        	| Parsed Clouds                       	|
|-------------	|-------------------------------------	|
| Description 	| Get Clouds based on Group selection 	|
| Type        	| Morpheus API                        	|
| Visibility  	| You Choose                          	|
| Option List 	| Clouds                              	|

Translation Script
```javascript
//Grab vCenter Clouds and Push Values
if (input.selectedGroup) {
for (var x = 0; x < data.length; x++) {
    results.push({name:data[x].name, value:data[x].id});
  }
}
```
Request Script
```javascript
if (input.selectedGroup) {
  results.siteId = input.selectedGroup
}
```

### Option Type Configuration

| Name                     	| Parsed Cloud               	|
|--------------------------	|----------------------------	|
| Description              	| Cloud Selected by the User 	|
| Field Name               	| parsedCloud                	|
| Export As Tag            	| You Choose                 	|
| Dependent Field          	| selectedGroup              	|
| Visibility Field         	|                            	|
| Display Value on Details 	|                            	|
| Type                     	| Select List                	|
| Label                    	| Cloud                      	|
| Default Value            	|                            	|
| Help Block               	|                            	|
| Required                 	| Yes                        	|
| Option List              	| Parsed Clouds              	|

## Networks

### Option List Configuration

| Name        	| Parsed Networks                                 	|
|-------------	|-------------------------------------------------	|
| Description 	| Get Networks based on Group and Cloud selection 	|
| Type        	| Morpheus API                                    	|
| Visibility  	| You Choose                                      	|
| Option List 	| Networks                                        	|

Translation Script
```javascript
if (input.parsedCloud && input.selectedGroup) {
for (var x = 0; x < data.length; x++) {
    results.push({name:data[x].name, value:data[x].id});
  }
}
```
Request Script
```
if (input.parsedCloud && input.selectedGroup){
  results.cloudId = input.parsedCloud
  results.groupId = input.selectedGroup
}
```

### Option Type Configuration

| Name                     	| Parsed Network               	|
|--------------------------	|------------------------------	|
| Description              	| Network Selected by the User 	|
| Field Name               	| parsedNetwork                	|
| Export As Tag            	| You Choose                   	|
| Dependent Field          	| parsedCloud                  	|
| Visibility Field         	|                              	|
| Display Value on Details 	|                              	|
| Type                     	| Select List                  	|
| Label                    	| Network                      	|
| Default Value            	|                              	|
| Help Block               	|                              	|
| Required                 	| Yes                          	|
| Option List              	| Parsed Networks              	|
