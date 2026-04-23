

**Pruebas Contrato:**



Caso  Validar Schema Booking:



pm.test("Status 200", function () { 

&#x20;   pm.response.to.have.status(200); 

}); 

const schema = { 

&#x20;   type: "object", 

&#x20;   properties: { firstname: { 

&#x20;       type: "string" }, 

&#x20;       lastname: { type: "string" }, 

&#x20;       totalprice: { type: "number" },

&#x20;       depositpaid: { type: "boolean" }, 

&#x20;       bookingdates: { 

&#x20;           type: "object", 

&#x20;           properties: { 

&#x20;               checkin: { type: "string" }, 

&#x20;               checkout: { type: "string" } 

&#x20;               }, 

&#x20;               required: \["checkin", "checkout"] 

&#x20;           }, 

&#x20;           additionalneeds: { type: "string" } 

&#x20;           }, 

&#x20;           required: \[ 

&#x20;               "firstname", 

&#x20;               "lastname", 

&#x20;               "totalprice", 

&#x20;               "depositpaid", 

&#x20;               "bookingdates" 

&#x20;           ] 

&#x20;       }; 

pm.test("Schema Booking válido", function () { pm.response.to.have.jsonSchema(schema); 

});





Caso  Validar Schema Lista:



pm.test("Status 200", function () { 

&#x20;   pm.response.to.have.status(200); 

});

let data = pm.response.json(); 



pm.test("Respuesta es arreglo", function () { pm.expect(data).to.be.an("array"); 

}); 

pm.test("Cada item tiene bookingid", function () { pm.expect(data\[0]).to.have.property("bookingid"); 

});



Caso  Validar Tipos de Datos:



pm.test("Status 200", function () {

&#x20;   pm.response.to.have.status(200);

});



if (pm.response.code === 200) {

&#x20;   let json = pm.response.json();



&#x20;   pm.test("firstname es string", function () {

&#x20;       pm.expect(json.firstname).to.be.a("string");

&#x20;   });



&#x20;   pm.test("lastname es string", function () {

&#x20;       pm.expect(json.lastname).to.be.a("string");

&#x20;   });



&#x20;   pm.test("totalprice es number", function () {

&#x20;       pm.expect(json.totalprice).to.be.a("number");

&#x20;   });

}



Caso  No Existe Booking ID:



{{baseUrl}}/booking/9999999

pm.test("404 esperado", () => { 

&#x20;   pm.expect(pm.response.code).to.eql(404); 

});



Caso  Payload Invalido:

{ 

&#x20;   "firstname": 123, 

&#x20;   "lastname": true 

}



pm.test("La API responde controladamente", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[200,400,500]); 

});



Caso  JSON Mal Formado:



{ 

&#x20;   "firstname": "Juan", 

&#x20;   "lastname": "Perez,



pm.test("Error por JSON inválido", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[400,500]); 

});





Caso  PUT Sin Body



pm.test("Método inválido rechazado", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[404,405]); 

});



Caso  Método No Permitido:

pm.test("Método inválido rechazado", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[404,405]); 

});



Caso  DELETE Sin Token:

pm.test("No autorizado", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});







