**Pruebas de Rendimiento:**

Caso  GET Booking:



pm.test("Status correcto", function () { 

&#x20;   pm.expect(pm.response.code).to.eql(201); 

}); 

pm.test("Tiempo menor a 1000 ms", function () { 

&#x20;   pm.expect(pm.response.responseTime).to.be.below(1000); 

});





Caso  GET Booking ID:



pm.test("Status 200", function () { pm.response.to.have.status(200); 

}); 

pm.test("Tiempo aceptable", function () { 

&#x20;   pm.expect(pm.response.responseTime).to.be.below(1000); 

});



{ 

&#x20;   "firstname": "Perf", 

&#x20;   "lastname": "Test", 

&#x20;   "totalprice": 150, 

&#x20;   "depositpaid": true, 

&#x20;   "bookingdates": { 

&#x20;       "checkin": "2026-09-01", 

&#x20;       "checkout": "2026-09-03" 

&#x20;   }, 

&#x20;   "additionalneeds": "None" 

}



pm.test("Status 200", function () { 

&#x20;   pm.response.to.have.status(200); 

}); 

pm.test("POST menor a 1000 ms", function () { 

&#x20;   pm.expect(pm.response.responseTime).to.be.below(1000); 

});









