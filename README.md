# forgambs_tutorial_nodejs

isso faz com que passe dados pra pagina index seguindo a rota 
com isso tb da pra carregar outras coisas em uma so pagina

Passando dados do server.js pra app_index.html
// server.js ######################################################################

const http      = require('http'); 

const express   = require('express');

const path      = require('path'); 


const app = express();

let getData = () => {

    //O seu método de leitura do arquivo vem aqui
    
    return 'qualquer que seja o seu resultado aqui';
}

app.get('/data', (req, res) => {
    res.send(getData());
});

app.get('/', (req, res) => {
    res.sendFile(path.join(__dirname+'/index.html'));
});

http.createServer(app).listen(8080, () => {

    console.log('server funcionando');
    
});

// index.html ###############################################################################

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <script src="http://code.jquery.com/jquery-1.11.0.min.js"></script>
    <script>
        $(document).ready(function() {
            $.get('/data', function(res) {
                $('span').html(res);
            })
        });
    </script>
</head>
<body>
    <p>Minha data: <strong><span></span><strong></p>
</body>
</html>
