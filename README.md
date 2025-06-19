<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <style>
    body {
      margin: 0;
      font-size: 36px;
      color: white;
      background: transparent;
      font-family: Arial, sans-serif;
    }
  </style>
</head>
<body>
  <div id="output">Lade Bestellungen...</div>

  <script>
    async function fetchSheet() {
      try {
        const res = await fetch('[DEIN_GOOGLE_SHEET_CSV_LINK](https://docs.google.com/spreadsheets/d/e/2PACX-1vQdSj0RbxYCxSztdK0zlPzZAvR_R2xrG5qLRHU6uJBcG4bNKcJhLlTzXNf4i-TrV9DDXsGoCFi0qMvp/pubhtml?gid=0&single=true)');
        const text = await res.text();
        const rows = text.trim().split("\n");
        const last = rows[rows.length - 1].split(",");
        document.getElementById("output").innerText =
          `🛍️ Danke an ${last[0]} für den Kauf von ${last[1]}!`;
      } catch (e) {
        document.getElementById("output").innerText = "Fehler beim Laden";
      }
    }
    fetchSheet();
    setInterval(fetchSheet, 15000); // alle 15 Sekunden aktualisieren
  </script>
</body>
</html>
