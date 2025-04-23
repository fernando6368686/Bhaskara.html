<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora De Bhaskara</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: black;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .calculator {
            background-color: yellow;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input {
            margin: 5px 0;
            padding: 8px;
            width: 200px;
            font-size: 16px;
            border-radius: 4px;
            border: 1px solid black;
        }
        button {
            padding: 10px 20px;
            background-color: gray;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
        }
        button:hover {
            background-color: black;
        }
        .result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <h2>Calculadora De Bhaskara</h2>
        <p>Digite os coeficientes da equação do segundo grau: <i></i></p>
        <form id="bhaskaraForm">
            <input type="number" id="a" placeholder="Valor de a" required>
            <input type="number" id="b" placeholder="Valor de b" required>
            <input type="number" id="c" placeholder="Valor de c" required>
            <br>
            <button type="button" onclick="calcularBhaskara()">Calcular</button>
        </form>

        <div class="result" id="result"></div>
    </div>

    <script>
        function calcularBhaskara() {
            // Obtém os valores dos coeficientes a, b e c
            const a = parseFloat(document.getElementById('a').value);
            const b = parseFloat(document.getElementById('b').value);
            const c = parseFloat(document.getElementById('c').value);
            
            // Verifica se a é 0, pois não é uma equação do segundo grau
            if (a === 0) {
                document.getElementById('result').innerHTML = "O valor de 'a' não pode ser zero.";
                return;
            }
            
            // Calcula o discriminante (Δ)
            const delta = (b * b) - (4 * a * c);
            
            // Exibe o valor de Δ
            let resultado = `<p>Discriminante (Δ) = ${delta}</p>`;

            // Se o discriminante for negativo, as raízes são complexas
            if (delta < 0) {
                resultado += `<p>As raízes são complexas.</p>`;
            } else {
                // Calcula as raízes reais
                const raiz1 = (-b + Math.sqrt(delta)) / (2 * a);
                const raiz2 = (-b - Math.sqrt(delta)) / (2 * a);
                
                if (delta === 0) {
                    resultado += `<p>Existe uma raiz real: x = ${raiz1}</p>`;
                } else {
                    resultado += `<p>As raízes reais são:</p>`;
                    resultado += `<p>x₁ = ${raiz1}</p>`;
                    resultado += `<p>x₂ = ${raiz2}</p>`;
                }
            }

            // Exibe o resultado
            document.getElementById('result').innerHTML = resultado;
        }
    </script>

</body>
</html>
