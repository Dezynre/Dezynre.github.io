
<!doctype html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width initial-scale=1">
	<title>nairobi</title>
 <style>
 .wrapper{
	width: 95%;
	margin: 5px auto;
	text-align: center;
}
.item{
	margin: 20px;
	padding: 5px;
}
.header{
	background-color: rgb(108,128,147);
	color: rgb(255,255,255);
	margin-bottom: 25px;
}
h1{
	font-size: 27px;
	font-weight: bold;
	font-family: 'Dancing Script', cursive;
}
h2{
	font-size: 25px;
}

@media screen and (min-width: 700px){
	.wrapper{
		display: flex;
	}
	.item{
		flex-grow: 1;
	}
	.body .item{
		padding-bottom: 40px;
	}
}
.body .item{
	min-height: 200px;
	border: 1px solid rgb(108,128,147);
	box-shadow: 6px 6px 12px;
	padding-top: 0;
	padding-left: 0;
	padding-right: 0;

}
.body .item h2{
	color: rgb(255,255,255);
	background-color: rgb(108,128,147);	
}
.body.item:hover{
	transform: scale(.95,.95);
}

.body.item{
	transition: .25s all ease-in;
}
.footer{
	display: flex;
	justify-content: center;
	padding: 10px;
	margin-top: 20px;
}
p{
	color: rgb(108,128,147);
	font-size: 50px;
}
 </style>
</head>
<body>
	<header class="wrapper header">
		<h1 class="item">Nairobi City Currently</h1>
	</header>

	<section class="wrapper body">
		<div class="item">
			<span class="fal fa-sun-cloud"></span>
			<h2>Physical Condition</h2>
			<p id="condition"></p>
		</div>
		<div class="item">
			<h2>Humidity</h2>
			<p id="humidity"></p>
		</div>
		<div class="item">
			<h2>Temperature</h2>
			<p id="temperature"></p>
		</div>
	</section>

	<footer class="wrapper footer">
		<button class="button" id="btn">REFRESH</button>
	</footer>
	<script>
 

let button=document.querySelector("#btn");

button.addEventListener("click", ()=>{
		let condition=document.querySelector("#condition");
		let humidity=document.querySelector("#humidity");
		let temperature=document.querySelector("#temperature");
		fetch("http://api.openweathermap.org/data/2.5/weather?lat=-1.2833&lon=36.8167&APPID=05dec21edd849f280c3d7382a4fbfe82").then(function(res){
			return res.json();
		}).then(function(json){

			let descriptionNode=document.createTextNode(json.weather[0].description);
			condition.appendChild(descriptionNode);
			let humidityNode=document.createTextNode(json.main.humidity+"mmHg");
			humidity.appendChild(humidityNode);
			let temperatureNode=document.createTextNode(json.main.temp+"Kelvins");
			temperature.appendChild(temperatureNode);
			console.log(json);
		}).catch(function(err){
			console.log(`Error:\t${err.message}`);
		});
});

 </script>

</body>
</html>
