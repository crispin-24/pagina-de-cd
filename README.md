<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> mate con cris  </title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            text-align: center;
        }
        header {
            background-color: #333;
            color: lightblue;
            padding: 15px;
            font-size: 24px;
        }
        main {
            padding: 20px;
        }
        button {
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            margin-top: 20px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .exercise {
            margin-top: 20px;
            font-size: 18px;
        }
        .explanation {
            margin-top: 20px;
            text-align: left;
            font-size: 16px;
            color: #333;
            background-color: #f9f9f9;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #ddd;
        }
        select {
            padding: 10px;
            font-size: 16px;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <header>
        Bienvenido a mate con cris 
    </header>

    <main>
        <h2>Temas que estudiar:</h2>
        <ul>
            <li>Multiplicación de binomios</li>
            <li>Suma y resta de binomios</li>
            <li>Binomios al cuadrado</li>
        </ul>

        <h3>Selecciona el tipo de ejercicio:</h3>
        <select id="temaSeleccionado">
            <option value="multiplicacion">Multiplicación de binomios</option>
            <option value="sumaResta">Suma y resta de binomios</option>
            <option value="binomiosCuadrado">Binomios al cuadrado</option>
        </select>

        <h3>Generador de Ejercicios Interactivos</h3>
        <button onclick="generarEjercicio()">Generar ejercicio</button>
        <button onclick="mostrarExplicacion()">Mostrar explicación</button>

        <div class="exercise" id="ejercicio">
            <!-- El ejercicio generado aparecerá aquí -->
        </div>

        <div class="explanation" id="explicacion">
            <!-- Explicación del ejercicio -->
        </div>
    </main>

    <script>
        let ejercicioActual = null;

        function generarEjercicio() {
            const tema = document.getElementById("temaSeleccionado").value;
            
            let ejercicios;
            if (tema === "multiplicacion") {
                ejercicios = [
                    {
                        pregunta: "Multiplica (x + 2)(x + 3)",
                        respuesta: "x² + 5x + 6",
                        explicacion: `
                            <h4>Explicación:</h4>
                            <p>Para multiplicar (x + 2)(x + 3), utilizamos la propiedad distributiva:</p>
                            <ul>
                                <li><strong>Paso 1:</strong> Multiplicamos el primer término de cada binomio: x * x = x².</li>
                                <li><strong>Paso 2:</strong> Multiplicamos los términos exteriores: x * 3 = 3x.</li>
                                <li><strong>Paso 3:</strong> Multiplicamos los términos interiores: 2 * x = 2x.</li>
                                <li><strong>Paso 4:</strong> Multiplicamos los últimos términos de cada binomio: 2 * 3 = 6.</li>
                                <li><strong>Paso 5:</strong> Sumamos los términos: x² + 3x + 2x + 6 = x² + 5x + 6.</li>
                            </ul>
                            <p><strong>Resultado Final:</strong> x² + 5x + 6.</p>
                        `
                    }
                ];
            } else if (tema === "sumaResta") {
                ejercicios = [
                    {
                        pregunta: "Resuelve la suma (x + 4) + (x + 2)",
                        respuesta: "2x + 6",
                        explicacion: `
                            <h4>Explicación:</h4>
                            <p>Para sumar (x + 4) + (x + 2), agrupamos los términos semejantes:</p>
                            <ul>
                                <li><strong>Paso 1:</strong> Sumamos los términos con 'x': x + x = 2x.</li>
                                <li><strong>Paso 2:</strong> Sumamos los términos constantes: 4 + 2 = 6.</li>
                            </ul>
                            <p><strong>Resultado Final:</strong> 2x + 6.</p>
                        `
                    }
                ];
            } else if (tema === "binomiosCuadrado") {
                ejercicios = [
                    {
                        pregunta: "Calcula (x + 5)²",
                        respuesta: "x² + 10x + 25",
                        explicacion: `
                            <h4>Explicación:</h4>
                            <p>Para calcular (x + 5)², utilizamos la fórmula del cuadrado de un binomio:</p>
                            <p>(a + b)² = a² + 2ab + b²</p>
                            <ul>
                                <li><strong>Paso 1:</strong> Elevamos al cuadrado el primer término: x².</li>
                                <li><strong>Paso 2:</strong> Multiplicamos ambos términos y los multiplicamos por 2: 2 * x * 5 = 10x.</li>
                                <li><strong>Paso 3:</strong> Elevamos al cuadrado el segundo término: 5² = 25.</li>
                            </ul>
                            <p><strong>Resultado Final:</strong> x² + 10x + 25.</p>
                        `
                    }
                ];
            }

            const randomIndex = Math.floor(Math.random() * ejercicios.length);
            ejercicioActual = ejercicios[randomIndex];

            document.getElementById("ejercicio").innerHTML = `
                <p><strong>Ejercicio:</strong> ${ejercicioActual.pregunta}</p>
                <p><strong>Respuesta:</strong> ${ejercicioActual.respuesta}</p>
            `;
            document.getElementById("explicacion").innerHTML = ejercicioActual.explicacion;
        }

        function mostrarExplicacion() {
            if (ejercicioActual) {
                document.getElementById("explicacion").style.display = "block";
            } else {
                alert("Primero genera un ejercicio.");
            }
        }
    </script>

</body>
</html>
