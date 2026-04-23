**Pruebas de CRUD:**

Caso  CrearBooking:



{

&#x20; "firstname": "Juan",

&#x20; "lastname": "Perez",

&#x20; "totalprice": 250,

&#x20; "depositpaid": true,

&#x20; "bookingdates": {

&#x20;   "checkin": "2026-05-10",

&#x20;   "checkout": "2026-05-15"

&#x20; },

&#x20; "additionalneeds": "Breakfast"

}



pm.test("Booking creado", () => {

&#x20;   pm.response.to.have.status(200);

});



let json = pm.response.json();

pm.environment.set("bookingId", json.bookingid);





Caso  Consultar Booking:

pm.test("Consulta exitosa", () => { 

&#x20;   pm.response.to.have.status(200); 

}); 

pm.test("Nombre correcto", () => { 

&#x20;   pm.expect(pm.response.json().firstname).to.exist; 

});





Caso  Actualizar Booking:



{

&#x20; "firstname": "Carlos",

&#x20; "lastname": "Lopez",

&#x20; "totalprice": 500,

&#x20; "depositpaid": false,

&#x20; "bookingdates": {

&#x20;   "checkin": "2026-06-01",

&#x20;   "checkout": "2026-06-07"

&#x20; },

&#x20; "additionalneeds": "Lunch"

}



pm.test("Actualizado correctamente", () => { 

&#x20;   pm.response.to.have.status(200); 

});



Caso  Eliminar Booking:



pm.test("Eliminado correctamente", function () {

&#x20;   pm.response.to.have.status(201);

});









