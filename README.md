<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gioco dei Numeri</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin-top: 50px;
        }

        .container {
            background-color: white;
            width: 400px;
            margin: auto;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        input {
            padding: 8px;
            margin: 10px;
        }

        button {
            padding: 8px 15px;
            cursor: pointer;
        }

        #messaggi {
            margin-top: 20px;
            text-align: left;
        }

        p {
            margin: 5px 0;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Gioco dei Numeri</h1>

    <div id="faseNome">
        <p>Quale soprannome vorresti utilizzare?</p>
        <input type="text" id="nome">
        <button onclick="iniziaGioco()">Inizia</button>
    </div>

    <div id="faseGioco" style="display:none;">
        <p>Indovina il numero da 1 a 10</p>
        <input type="number" id="numero" min="1" max="10">
        <button onclick="controllaNumero()">Prova</button>
    </div>

    <div id="messaggi"></div>
</div>

<script>
    let nomeGiocatore = "";
    const numeroSegreto = 6;

    function aggiungiMessaggio(testo) {
        document.getElementById("messaggi").innerHTML += "<p>" + testo + "</p>";
    }

    function iniziaGioco() {
        nomeGiocatore = document.getElementById("nome").value;

        if (nomeGiocatore === "") {
            alert("Inserisci un soprannome!");
            return;
        }

        document.getElementById("faseNome").style.display = "none";
        document.getElementById("faseGioco").style.display = "block";

        aggiungiMessaggio("Buona fortuna " + nomeGiocatore + "!");
    }

    function controllaNumero() {
        let numeroInserito = parseInt(document.getElementById("numero").value);

        if (numeroInserito === numeroSegreto) {
            aggiungiMessaggio(nomeGiocatore + " hai indovinato! Hai vinto un abbraccio!");
            aggiungiMessaggio("GIOCO TERMINATO!");
            document.getElementById("faseGioco").style.display = "none";
        }
        else if (numeroInserito > numeroSegreto) {
            aggiungiMessaggio("Prova un po' di meno!");
        }
        else {
            aggiungiMessaggio("Prova un po' di più!");
        }

        document.getElementById("numero").value = "";
    }
</script>

</body>
</html>
