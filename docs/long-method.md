## Long Method
 can limit one method to ten line
 the more lines found in a method, the harder it is to figure out what the method does. 

 solution: 
 
 1. extract method to less code duplication , isolates independent parts of code , more readable code.
 ``` 
 function logDetail(method) {
   this.method = method;
   this.method.name = 'tester';
   console.log(this.method.name);
   console.log(this.method.args);
 }
 ```
 extract two method.
 ```
 function changeName(method) {
  method.name = 'test';
 }
 function log(method) {
  console.log(method.name);
   console.log(method.args);
 }
 ```
 2. if local variables and parameters interfere with extracting method.
 use replace temp with Query 
 
 ```
  function calculateTotal() {
    var basePrice = quantity * itemPrice;
    if (basePrice > 100 ) {
       return basePrice * 0.95;
    } else {
       return basePrice * 0.98;
    }
  }
 ```
 move the entile expression to separate method . 
 
 ```
 function basePrice() {
   return quantity * itemPrice;
 }
 function calculateTotal() {
   if(basePrice() > 100 ) {
     return basePrice() * 0.95;
   } else {
     return basePrice() * 0.98;
   }
 }
 ```
 3. Introduce parameter Object
 
 ```
 function getDate(startDate, endDate) {
   return new Date(startDate - endDate);
 }
 function getDate(dateRange) {
   return new Date(dateRange.startDate - dateRange.endDate);
 }
 ```
 4. Preserve Whole Object. 
   
 5. moving the entire method to separate object with replace method with method object.
 
 6 decompose conditional if you have complex conditonal like if/else/switch 
 
 ```
 if(date.isBefore(summer_start) || date.isAfter(summer_end)) {
    charge = quantity * winterRate + winterServiceCharge;
 } else {
    charge = quantity * summerRate;
 }
 
 if (notSummer(date)) {
   charge = winterCharge(quantity);
 } else {
   charge = summerCharge(quantity);
 }
