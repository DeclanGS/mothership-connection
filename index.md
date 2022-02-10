<html>
<body>

<button type="button" onclick="newChar()">Generate New</button>

<p id="character">Who's up?</p>

<script src="mothership.js">

function newChar() { 
	document.getElementById("character").innerHTML = main()
}
</script>

</body>
</html>

