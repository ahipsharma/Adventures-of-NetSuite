# Adventures-of-NetSuite
![NetSuite](https://github.com/ahipsharma/Adventures-of-NetSuite/assets/76726757/f9771583-7f01-48c4-a54a-81336bfa78df)


## Hola peeps!!! Struggling with NetSuite??? Search here might find a solution for your query



### Getting Script paramters

Import - 'N/runtime'module

var myScript = runtime.getCurrentScript();
var scriptParameterValue = myScript.getParameter({
    name: 'INERNAL_ID_OF_THE_PARAMETER_PASSED'
});
