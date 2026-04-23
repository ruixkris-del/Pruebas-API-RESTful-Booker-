**Pruebas de Humo:**



Caso Ping:



pm.test("Status 201", () => { 

&#x20;   pm.response.to.have.status(201); 

}); 

pm.test("Tiempo menor a 1000ms", () => { pm.expect(pm.response.responseTime).to.be.below(1000);

});



Caso Obtener Booking:



pm.test("Status 200", () => { 

&#x20;   pm.response.to.have.status(200);

});

pm.test("Retorna arreglo", () => {

&#x20;   pm.expect(pm.response.json()).to.be.an("array"); 

});



Caso  Obterner Booking ID:



pm.test("Status 200", function () {

&#x20;   pm.response.to.have.status(200);

});



var json = pm.response.json();



pm.test("Respuesta es objeto JSON", function () {

&#x20;   pm.expect(json).to.be.an("object");

});



pm.test("Tiene firstname", function () {

&#x20;   pm.expect(json.firstname).to.exist;

});



pm.test("Tiene lastname", function () {

&#x20;   pm.expect(json.lastname).to.exist;

});



pm.test("Tiene totalprice", function () {

&#x20;   pm.expect(json.totalprice).to.exist;

});



pm.test("Tiempo menor a 1000 ms", function () {

&#x20;   pm.expect(pm.response.responseTime).to.be.below(1000);

});



Caso Generar Token:



{ 

&#x20;   "username": "admin", 

&#x20;   "password": "password123" 

}



pm.test("Status 200", () => { 

&#x20;   pm.response.to.have.status(200); 

}); 

let json = pm.response.json(); 

pm.environment.set("token", json.token); 

pm.test("Token creado", () => { 

&#x20;   pm.expect(json.token).to.exist; 

});

