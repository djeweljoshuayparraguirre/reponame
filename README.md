# cmsc126
For GitHub Repository

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>UP Mindanao Sign-up</title>
	<link rel="stylesheet" href="https://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
	<link rel="stylesheet" href="https://resources/demos/style.css">
	<script src="https://code.jquery.com/jquery-1.12.4.js"></script>
	<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>
</head>
<style>
body{
	background-color:#800000;
}
h1 {text-align: center;}
p {text-align: center;color: white;}
div {text-align: center;}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
input {
	border-radius: 5px;
	width: 200px;
	height: 30px;
)

</style>
<body>

<img src="UPMIN.png" style="width:170px;height:160px;" class="center">
<br>
<form>

<div class="row">
  <div class="col1">
    <p><label for="fname" style="font-size:20px">First Name</label></p>
  </div>
  <div class="col2">
    <input name="fname" id="fname" required><br>
  </div>
</div>


<div class="row">
  <div class="col1">
    <p><label for="mname" style="font-size:20px">Middle Name</label></p>
  </div>
  <div class="col2">
    <input name="mname" id="mname" required><br>
  </div>
</div>


<div class="row">
  <div class="col1">
    <p><label for="lname" style="font-size:20px">Last Name</label></p>
  </div>
  <div class="col2">
    <input name="lname" id="lname" required><br>
  </div>
</div>


<div class="row">
  <div class="col1">
   <p><label style="font-size:20px">Gender:</label></p>
  </div>
  <div class="col2" id="gender">
	<p><input class="radio" type="radio" checked="checked" name="gender" id="genderMale" value="M" style="width:30px">
	<label for="radio-1" style="font-size:20px">Male</label></p>
	<p><input type="radio" checked="checked" name="gender" value="F" style="width:30px">
	<label for="radio-2" style="font-size:20px">Female</label></p>
  </div>
</div>

<div class="row">
  <div class="col1">
<p style="font-size:20px">Date of Birth</p>
<input type="text" id="datepicker">

  </div>
</div>

<div class="row">
  <div class="col1">
    <p><label for="tags" style="font-size:20px">Province</label></p>
  </div>
  <div class="col2">
    <input name="tags" id="tags" required><br>
  </div>
</div>
<br>
<div class="row">
  <div class="col1">
    <p><label for="year" style="font-size:20px">Year Level in UPMin</label></p>
  </div>
  <div class="col2">
    <input name="year" id="spinner" min="1" required><br>
  </div>
</div>

<p>
<button onclick="saveFile()" style="font-size:20px">Submit</button>
</p>
</form>
<script>
$( function(){
	$("genderMale").checkboxradio();
	$( "#datepicker" ).datepicker();
	var availableTags = [
	"Agusan del Norte",
	"Agusan del Sur",
	"Alabel",
	"Basilan",
	"Bukidnon",
	"Camiguin",
	"Compostela Valley",
	"Davao del Norte",
	"Davao del Sur",
	"Davao Occidental",
	"Davao Oriental",
	"Dinagat Islands",
	"Lanao del Norte",
	"Lanao del Sur",
	"Maguindanao",
	"Misamis Occidental",
	"Misamis Oriental",
	"North Cotabato", 
	"South Cotabato",  
	"Sultan Kudarat",
	"Sulu",
	"Surigao del Norte",
	"Surigao del Sur",
	"Tawi-Tawi",
	"Zamboanga del Norte",
	"Zamboanga del Sur",
	"Zamboanga Sibugay"
	];
	$("#tags").autocomplete({
		source: availableTags
	});
	});
$("#spinner").spinner();
    let saveFile = () => {
    	
        // Get the data from each element on the form.
    	const fname = document.getElementById('fname');
        const mname = document.getElementById('mname');
        const lname = document.getElementById('lname');
		const birth = document.getElementById('datepicker');
        const province = document.getElementById('tags');
		const year = document.getElementById('spinner');
        
	
        // This variable stores all the data.
        let data = 
            '\r First Name: ' + fname.value + ' \r\n ' + 
            'Middle Name: ' +mname.value + ' \r\n ' + 
            'Last Name: ' + lname.value + ' \r\n ' + 
            'Gender: ' + ($("#genderMale").is(":checked")?"Male":"Female") + ' \r\n ' + 
			'Date of Birth: ' + birth.value + ' \r\n ' + 
			'Province: ' + province.value + ' \r\n ' + 
            'Year Level in UPMin: ' + year.value;
        
        // Convert the text to BLOB.
        const textToBLOB = new Blob([data], { type: 'text/plain' });
        const sFileName = 'formData.txt';	   // The file to save the data.

        let newLink = document.createElement("a");
        newLink.download = sFileName;

        if (window.webkitURL != null) {
            newLink.href = window.webkitURL.createObjectURL(textToBLOB);
        }
        else {
            newLink.href = window.URL.createObjectURL(textToBLOB);
            newLink.style.display = "none";
            document.body.appendChild(newLink);
        }

        newLink.click(); 
    }
</script>

</body>
</html>
