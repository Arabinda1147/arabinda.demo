<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Time and Date</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #541818;
        }
        #date {
            font-size: 1.5rem;
            color: #cd630d;
        }
        #clock {
            font-size: 2rem;
            font-weight: bold;
            color: #6aa911;
        }
    </style>
</head>
<body>
    <div id="date"></div>
    <div id="clock"></div>
    
    <script>
        function updateDateTime() {
            const now = new Date();
            
            // Format date as Weekday, Month Day, Year
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const formattedDate = now.toLocaleDateString(undefined, options);
            document.getElementById('date').textContent = formattedDate;

            // Format time as HH:MM:SS
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            document.getElementById('clock').textContent = `${hours}:${minutes}:${seconds}`;
        }

        // Update every second
        setInterval(updateDateTime, 1000);
        // Initialize immediately
        updateDateTime();
    </script>
</body>
</html>
