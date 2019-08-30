# Swagger Test Templates
Install via npm

    npm install --save swagger-test-templates
Create a mock api 
[https://www.mockapi.io/projects/5d662961520e1b00141ede67](https://www.mockapi.io/projects/5d662961520e1b00141ede67)

Using swagger inspector generate API definition for your Mock Api
[https://inspector.swagger.io/builder](https://inspector.swagger.io/builder)

Use your [Swagger](http://swagger.io/) API definition file to generate test for your API.

    var stt = require('swagger-test-templates');
    var swagger = require('/path/to/swagger.json'');
    var config = {
      assertionFormat: 'should',
      testModule: 'supertest',
      pathName: ['/user', '/user/{id}'],
      loadTest: [{pathName:'/user', operation:'get', load:{requests: 1000, concurrent: 100}}, { /* ... */ }],
      maxLen: 80
    };
    var tests = stt.testGen(swagger, config);
    const fs = require('fs'); 
    test = tests[0].test;
    filename = tests[0].name;
    fs.writeFile(filename, test, function(err) {
        if(err) {
            return console.log(err);
        }
    
        console.log("The file was saved!");
    });



