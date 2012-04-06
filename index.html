var app = require('http').createServer(handler),
  io = require('socket.io').listen(1337),
   fs = require('fs'),
   jsdom = require("jsdom");

  var ciudades = {
      "Madrid":"MADRI",
      "Cuenca":"CUENC",
      "Guadalajara":"GUADA",
      "Valencia":"VALEN"
   };



app.listen(8000);

function handler (req, res) {
  fs.readFile(__dirname + '/index.html',
  function (err, data) {
    if (err) {
      res.writeHead(500);
      return res.end('Error loading index.html');
    }

    res.writeHead(200, {
        "Content-Type": "text/html"
      });
    res.end(data);
  });
}

io.sockets.on("connection", function(socket) {
  
  socket.on("travel", function(data) {
    var renfeQuery = generateQuery(data.origen,data.destino,data.year,data.month,data.day);
    var trenJson = {
      "tipo":null,
      "ruta":{
        "origen":null,
        "destino":null
      },
      "tiempo":{
        "salida":null,
        "llegada":null,
        "duracion":null
      },
      "precios":null
    },
    precio={"tipo":null,
        "cantidad":null};
      

    var i=0;
    var trenes=new Array(); //necesario!!
    var trenesJson=new Array();
    jsdom.env("http://horarios.renfe.com/HIRRenfeWeb/buscar.do?O=MADRI&D=CUENC&AF=2012&MF=04&DF=30", [
      'http://code.jquery.com/jquery-1.5.min.js'
       ],
        function(errors, window) {
          //eliminar
          trenJson.ruta.origen="Madrid";
          trenJson.ruta.destino="Cuenca";
           console.log("Working");
           var $ = window.$;
           $("table#row > tbody > tr").each(function(){
            var children = $(this).children("td");// importante el $(this)
            var tren =$(children[0]).text().trim();
            tren=tren.replace(/[0-9]+/,"");
            tren=tren.trim();
            console.log("Tren: "+tren+" ");
            trenJson.tipo=tren;

            var depTime=$(children[1]).text().trim();
            tren=tren.concat(" ("+depTime+") ");
            console.log("Hora de salida: "+depTime);
            trenJson.tiempo.salida=depTime;

            var arrTime=$(children[2]).text().trim();
            tren=tren.concat(" ("+arrTime+")");
            console.log("Hora de llegada: "+arrTime);
            trenJson.tiempo.llegada=arrTime;

            var duration=$(children[3]).text().trim();
            tren=tren.concat(" in "+duration+" ");
            console.log("Duracion: "+duration);
            trenJson.tiempo.duracion=duration;

            //tbody casca!!!
            var n=-1;
            var ntr=$(children[4]).find("table tr#divcont").size();
            tren=tren.concat("Precios: ");
            trenJson.precios=new Array();
            $(children[4]).find("table tr#divcont").each(function(){
              
              var m=0;
             
              n++;
              var ntd=$(this).find("td").size();
              $(this).find("td").each(function(index){
                console.log("tr: "+n+" de "+ ntr+" / td: "+m +" de " + ntd);
                console.log($(this).text());
                if(m==1 || m==2){
                  tren=tren.concat($(this).text()+" ");
                }
                if(m==1){
                  precio.tipo=($(this).text());
                 
                }
                if(m==2){
                  precio.cantidad=($(this).text());
                  trenJson.precios[n]=precio;

                }
                m++;
              });
            });
            n++;

            tren=tren.concat("\n");
            trenes[i]=tren;
            trenesJson[i]=trenJson;
            i++;
            
            console.log(JSON.stringify(trenesJson));
            console.log("Tren scrapped\n\n\n\n\n");
                  
    });
      socket.emit("query", {renfeQuery: renfeQuery,mresponse:trenes,jsonResponse:trenesJson});
});

  });
});

function generateQuery( origin, destination, year, month, day){

    var res = "http://horarios.renfe.com/HIRRenfeWeb/buscar.do";
    res = res.concat("?");
    res = res.concat("O");
    res = res.concat("=");
    res = res.concat(ciudades[origin]);
    res = res.concat("&");
    res = res.concat("D");
    res = res.concat("=");
    res = res.concat(ciudades[destination]);
    res = res.concat("&");
    res = res.concat("AF");
    res = res.concat("=");
    res = res.concat(year);
    res = res.concat("&");
    res = res.concat("MF");
    res = res.concat("=");
    res = res.concat(month);
    res = res.concat("&");
    res = res.concat("DF");
    res = res.concat("=");
    res = res.concat(day);
    
    
    return res;
}




