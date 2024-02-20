<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Juego Sanrio de Química con Kuromi</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #fff5f5; /* Fondo rosa suave */
            text-align: center;
            margin: 20px;
        }

        h1 {
            color: #ff66b2; /* Rosa brillante */
        }

        h2 {
            color: #ff66b2; /* Rosa brillante */
        }

        div {
            background-color: #ffffff;
            padding: 20px;
            margin: 10px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1); /* Sutil sombra */
        }

        input {
            padding: 10px;
            margin: 10px;
            border: 1px solid #ff66b2; /* Borde rosa */
            border-radius: 5px;
            width: 60%;
        }

        button {
            padding: 10px 20px;
            background-color: #ff66b2; /* Rosa brillante */
            color: #fff; /* Texto blanco */
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #e60073; /* Rosa más oscuro al pasar el ratón */
        }

        #kuromi {
            max-width: 100%;
            border-radius: 10px;
            margin-top: 20px;
            display: none;
        }

        #correcto,
        #incorrecto {
            max-width: 100%;
            border-radius: 10px;
            display: none;
        }

        #pregunta1,
        #pregunta2,
        #resultado {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
    </style>
</head>

<body>
    <h1>Juego Sanrio de Química con Kuromi</h1>

    <div id="pregunta1">
        <h2 style="color: #ffcc80;">Pregunta 1: ¿Cuántos electrones tiene un átomo de hidrógeno?</h2>
        <input type="text" id="respuesta1" placeholder="Ingresa tu respuesta">
        <button onclick="verificarRespuesta(1)">Verificar</button>
    </div>

    <div id="pregunta2" style="display: none;">
        <h2 style="color: #ffcc80;">Pregunta 2: ¿Cuántos átomos de oxígeno hay en una molécula de agua (H<sub>2</sub>O)?</h2>
        <input type="text" id="respuesta2" placeholder="Ingresa tu respuesta">
        <button onclick="verificarRespuesta(2)">Verificar</button>
    </div>

    <div id="resultado" style="display: none;">
        <h2 id="mensajeResultado"></h2>
        <img src="https://www.pngtank.com/storage/thumbnails/64970e2199550.png" alt="Kuromi" id="kuromi">
        <img src="" alt="Respuesta Correcta" id="correcto">
        <img src="https://i.pinimg.com/originals/5e/62/fc/5e62fcdcaa6fac15f1db688b7d20401e.gif" alt="Respuesta Incorrecta" id="incorrecto">
    </div>

    <script>
        var preguntaActual = 1;
        var totalPreguntas = 2; // Ajusta el total de preguntas según sea necesario

        var respuestasCorrectas = {
            1: '1',  // Respuesta correcta para la pregunta 1
            2: '1'   // Respuesta correcta para la pregunta 2
            // Agrega más respuestas según sea necesario
        };

        function verificarRespuesta(numeroPregunta) {
            var respuestaUsuario = document.getElementById('respuesta' + numeroPregunta).value.trim().toLowerCase();
            var respuestaCorrecta = respuestasCorrectas[numeroPregunta];

            if (respuestaUsuario === respuestaCorrecta) {
                mostrarResultado(true);
                pasarSiguientePregunta();
            } else {
                mostrarResultado(false);
            }
        }

        function mostrarResultado(esCorrecto) {
            var mensajeResultado = document.getElementById('mensajeResultado');
            var kuromiImagen = document.getElementById('kuromi');
            var correctoImagen = document.getElementById('correcto');
            var incorrectoImagen = document.getElementById('incorrecto');

            if (esCorrecto) {
                mensajeResultado.textContent = '¡Respuesta Correcta!';
                kuromiImagen.style.display = 'block';
                correctoImagen.style.display = 'block';
                incorrectoImagen.style.display = 'none';
            } else {
                mensajeResultado.textContent = 'Respuesta Incorrecta';
                kuromiImagen.style.display = 'none';
                correctoImagen.style.display = 'none';
                incorrectoImagen.style.display = 'block';
            }

            document.getElementById('resultado').style.display = 'flex';
        }

        function pasarSiguientePregunta() {
            preguntaActual++;

            if (preguntaActual <= totalPreguntas) {
                var preguntaActualDiv = document.getElementById('pregunta' + preguntaActual);
                var preguntaAnteriorDiv = document.getElementById('pregunta' + (preguntaActual - 1));

                preguntaAnteriorDiv.style.display = 'none';
                preguntaActualDiv.style.display = 'flex';
            } else {
                // Todas las preguntas respondidas
                mostrarFelicitacion();
            }
        }

        function mostrarFelicitacion() {
            var resultadoDiv = document.getElementById('resultado');
            resultadoDiv.style.display = 'none'; // Oculta la sección de resultados
            
            var felicitacionDiv = document.createElement('div');
            felicitacionDiv.innerHTML = '<h2>FELICIDADES, SABES MÁS DE QUÍMICA QUE NOÉ</h2><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTx60loDzak7ZHnPKMJPOvAya3_6cL1XgWq6g&usqp=CAU" alt="Felicitación">';
            
            document.body.appendChild(felicitacionDiv);
        }
    </script>
</body>

</html>
