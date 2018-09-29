<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>repl.it</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/css/bootstrap.min.css" integrity="sha384-9gVQ4dYFwwWSjIDZnLEWnxCjeSWFphJiwGPXr1jddIhOegiu1FwO5qRGvFXOdJZ4" crossorigin="anonymous">

    <style>
      .col-sm {border: solid blue 3px;}
    </style>

  </head>
  <body>

<div class="container">
  <div class="row">
    <div class="col-sm">
      First column
    </div>
    <div class="col-sm">
      Second column
    </div>
    <div class="col-sm">
      Third column
    </div>
  </div>
</div>

  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  
  <script>
    $(document).ready(function(){
      $.get("https://data.cityofchicago.org/resource/rp42-fxjt.json", function(response) {
        console.log(response);
        var row = $("<div>").addClass("row");

        $.each(response, function(i,v) {
            console.log(i,v);
            var cell = $("<div>");
            cell.addClass("col-sm");
            cell.html(v.make + "<br>" + v.color + "<br>" + v.plate + "<br>" + v.state);
            
            row.append(cell);
            
            if (row.find("div").length == 3) {
              $(".container").append(row);
              row = $("<div>").addClass("row");
            }            
        });

        if (row.find("div").length != 0) {
              $(".container").append(row);
        }            


      });
    });
  </script>

  </body>
</html>
