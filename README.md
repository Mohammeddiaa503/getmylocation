
<!DOCTYPE html>
<html>
<head>
  <title>Geolocation Form Submission</title>
  <script>
    function getLocationAndSubmit() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
      } else {
        alert("Geolocation is not supported by this browser.");
      }
    }

    function showPosition(position) {
      var latitude = position.coords.latitude;
      var longitude = position.coords.longitude;
      var locationLink = `https://maps.google.com/?q=${latitude},${longitude}`;
      
      // Replace 'YOUR_FORM_URL' with the pre-filled URL of your form
      var formURL = `https://docs.google.com/forms/d/e/1FAIpQLScnJohKKEz0VjE_OcopTpwvJ867T3XlxDrkyTEA_pA__DpQXQ/viewform?usp=pp_url&entry.1660578133=${encodeURIComponent(locationLink)}`;

      // Redirect to the form with the pre-filled URL
      window.location.href = formURL;
    }

    function showError(error) {
      alert(`Unable to retrieve your location due to ${error.message}`);
    }
  </script>
</head>
<body onload="getLocationAndSubmit()">
  <p>Redirecting to form...</p>
</body>
</html>
