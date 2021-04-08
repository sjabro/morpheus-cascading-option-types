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

```javascript Translation Script
//Grab All Groups and Push Values

for (var x = 0; x < data.length; x++) {
results.push({name:data[x].name, value:data[x].id});
    }
```
```javascript Request Script

```
