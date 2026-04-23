**Pruebas de Seguridad:**



Caso  PUT Sin Autenticación:



{ 

&#x20;   "firstname": "Intruso", 

&#x20;   "lastname": "Test", 

&#x20;   "totalprice": 111, 

&#x20;   "depositpaid": true, 

&#x20;   "bookingdates": { 

&#x20;       "checkin": "2026-01-01", 

&#x20;       "checkout": "2026-01-02" 

&#x20;       }, 

&#x20;       "additionalneeds": "None" 

}



pm.test("Acceso no autorizado", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});





Caso  PATCH Sin Autenticación:

{ 

&#x20;   "firstname": "Hack" 

}



pm.test("PATCH bloqueado sin token", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});





Caso  DELETE Sin Autenticación:



pm.test("DELETE bloqueado sin token", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});





Caso  PUT Token Invalido:



{ 

&#x20;   "firstname": "Intruso", 

&#x20;   "lastname": "Test", 

&#x20;   "totalprice": 111, 

&#x20;   "depositpaid": true, 

&#x20;   "bookingdates": { 

&#x20;       "checkin": "2026-01-01", 

&#x20;       "checkout": "2026-01-02" 

&#x20;       }, 

&#x20;       "additionalneeds": "None" 

}



pm.test("Token rechazado", () => { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});





Caso  DELETE Token Invalido:



pm.test("DELETE con token inválido rechazado", function () { 

&#x20;   pm.expect(pm.response.code).to.be.oneOf(\[401,403]); 

});















