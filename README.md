<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfil y Ranking | Johannes Goulenberg</title>
    <style>
        :root {
            --color-bg-dark: #1e1e1e;
            --color-bg-medium: #2c2c2c;
            --color-text-light: #f0f0f0; /* Blanco (para los puntos) */
            --color-primary: #FFD700;
            --color-secondary: #ffc107;
            --color-locked: #666; 
            --color-border: #444;
            --color-ranking-highlight: #4a4a4a;
        }

        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            line-height: 1.6; 
            margin: 0; 
            padding: 0; 
            background-color: var(--color-bg-dark); 
            color: var(--color-text-light);
        }
        
        header { 
            background: var(--color-bg-medium); 
            padding: 30px 0; 
            text-align: center; 
            border-bottom: 2px solid var(--color-primary);
        }
        header h1 { 
            margin: 0; 
            font-size: 2em; 
            color: var(--color-primary); 
        }
        /* Subtítulo Dorado */
        header h3 { 
            margin: 5px 0 0 0; 
            font-size: 1.1em;
            color: var(--color-primary); 
            font-weight: 300;
        }
        
        main { 
            padding: 40px 20px; 
            max-width: 900px; 
            margin: 30px auto; 
            background: var(--color-bg-medium); 
            border-radius: 8px; 
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
        }
        
        h2 { 
            color: var(--color-primary); 
            border-bottom: 1px solid var(--color-border); 
            padding-bottom: 10px; 
            margin-top: 30px;
            font-weight: 300;
        }

        .profile-header {
            text-align: center;
            padding: 20px 0;
            border-bottom: 1px solid var(--color-border);
            margin-bottom: 30px;
        }
        .profile-header h3 {
            font-size: 2.5em;
            margin-bottom: 5px;
            color: var(--color-primary); 
        }
        .profile-header p {
            color: var(--color-primary); 
            font-size: 1.1em;
            font-weight: 300;
        }


        .stats-grid {
            display: flex;
            justify-content: space-around;
            text-align: center;
            margin-top: 20px;
            margin-bottom: 30px;
        }
        .stat-item h4 {
            color: var(--color-primary);
            font-size: 2em;
            margin: 0;
        }
        .stat-item p {
            color: #aaa;
            margin-top: 5px;
            font-size: 0.9em;
        }

        .ranking-container {
            margin-top: 40px;
        }
        .ranking-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        .ranking-table th, .ranking-table td {
            padding: 12px 15px;
            border-bottom: 1px solid var(--color-border);
        }
        .ranking-table th {
            background-color: #333;
            color: var(--color-primary);
            font-weight: 600;
            text-transform: uppercase;
        }
        .ranking-table tbody tr:hover:not(.is-goulenberg) {
            background-color: #383838;
            cursor: pointer;
        }
        
        /* ESTILO PARA LOS PUNTOS - Columna 3 */
        .ranking-table tbody td:nth-child(3) {
            color: var(--color-text-light); /* Todos los puntos en blanco */
            font-weight: normal; 
        }

        .ranking-table tbody tr.is-goulenberg {
            background-color: var(--color-ranking-highlight);
            font-weight: bold;
            color: var(--color-primary); 
        }
        /* Los puntos de Goulenberg serán dorados por herencia de .is-goulenberg */
        .ranking-table tbody tr.is-goulenberg td:nth-child(3) {
            color: var(--color-primary); 
            font-weight: bold; 
        }


        .ranking-position-1, .ranking-position-2, .ranking-position-3, .ranking-position-4 {
            color: var(--color-primary);
            font-weight: bold;
        }
        
        /* ALINEACIÓN DE COLUMNAS */
        .ranking-table th:nth-child(1), .ranking-table td:nth-child(1) {
            width: 10%;
            text-align: center;
        }
        .ranking-table th:nth-child(2), .ranking-table td:nth-child(2) {
            width: 45%;
            text-align: left;
        }
        .ranking-table th:nth-child(3), .ranking-table td:nth-child(3) {
            width: 25%;
            text-align: right; 
        }
        .ranking-table th:nth-child(4), .ranking-table td:nth-child(4) {
            width: 20%;
            text-align: right;
        }
        
        .ver-mas {
            display: block;
            text-align: center;
            padding: 15px;
            margin-top: 15px;
            background-color: #333; 
            color: var(--color-primary); 
            border-radius: 4px;
            text-decoration: none;
            transition: transform 0.3s; 
            font-weight: bold;
        }
        .ver-mas:hover {
            background-color: #383838; 
            color: var(--color-primary);
            transform: scale(1.01); 
            cursor: pointer;
        }


        /* SECCIÓN DE LOGROS */
        .achievement-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        .achievement-card {
            background: #333;
            border-radius: 6px;
            padding: 15px;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
            position: relative; 
            overflow: hidden;
            height: auto; 
            transition: transform 0.3s ease, box-shadow 0.3s ease, background-color 0.3s;
            cursor: pointer;
        }
        
        /* EFECTO HOVER DE LOGROS */
        .achievement-card:hover {
            transform: translateY(-5px) scale(1.02);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.6);
            background-color: #383838;
        }

        .unlocked {
            border: 2px solid var(--color-secondary);
            color: var(--color-secondary);
        }
        .locked {
            border: 2px dashed var(--color-locked);
            color: var(--color-locked);
            opacity: 0.8;
            cursor: default;
        }

        .locked::before {
            content: "\1F512";
            font-size: 2.5em;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: var(--color-locked);
            opacity: 1; 
            z-index: 10;
        }
        
        .achievement-card h4 {
            margin: 0 0 5px 0;
            font-size: 1.1em;
            font-weight: 600;
        }
        
        .achievement-card p {
            display: block; 
            font-size: 0.75em;
            color: #ccc; 
            margin: 0;
            line-height: 1.3;
        }
        
        .locked h4, .locked p {
            filter: blur(1px); 
            z-index: 5;
            position: relative;
        }
        
    </style>
</head>
<body>

    <header>
        <h1>REACE</h1>
        <tr>
        </tr>
        <h3>Competir para Crecer, Aprender para Ganar</h3>
    </header>

    <main>
        
        <section class="profile-header">
            <h3>Johannes Goulenberg</h3>
            <p>Alumno de 2º de Bachillerato  Clase: A</p>

            <div class="stats-grid">
                <div class="stat-item">
                    <h4>4,120</h4>
                    <p>Puntos Totales</p>
                </div>
                <div class="stat-item">
                    <h4>#5</h4>
                    <p>Ranking General</p>
                </div>
                <div class="stat-item">
                    <h4>8</h4>
                    <p>Logros Desbloqueados</p>
                </div>
            </div>
        </section>
        
        <section class="ranking-container">
            <h2>Ranking General (Top 5)</h2>
            
            <table class="ranking-table">
                <thead>
                    <tr>
                        <th>Pos.</th>
                        <th>Alumno</th>
                        <th>Puntos</th>
                        <th>Logros</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="ranking-position-1">1</td>
                        <td>Alvin Hernandson</td>
                        <td>5,350</td>
                        <td>14</td>
                    </tr>
                    <tr>
                        <td class="ranking-position-2">2</td>
                        <td>George Riverside</td>
                        <td>5,100</td>
                        <td>12</td>
                    </tr>
                    <tr>
                        <td class="ranking-position-3">3</td>
                        <td>Xavi Crooked</td>
                        <td>5,010</td>
                        <td>11</td>
                    </tr>
                    <tr>
                        <td class="ranking-position-4">4</td>
                        <td>Paul Village</td>
                        <td>4,250</td>
                        <td>9</td>
                    </tr>
                    <tr class="is-goulenberg">
                        <td>5</td>
                        <td>Johannes Goulenberg</td>
                        <td>4,120</td>
                        <td>8</td>
                    </tr>
                </tbody>
            </table>
            
            <a href="#" onclick="return false;" class="ver-mas">Ver Ranking Completo (1-100)</a>
        </section>


        <section id="logros">
            <h2>Logros Desbloqueados y Potenciales</h2>
            
            <div class="achievement-grid">
                
                <div class="achievement-card unlocked" title="Ganar el desafío de cálculo rápido 3 veces consecutivas.">
                    <h4>Nivel Oro en Cálculo Mental</h4> 
                    <p>Ganar el desafío de cálculo rápido 3 veces consecutivas.</p>
                </div>
                
                <div class="achievement-card unlocked" title="Completar 5 proyectos colectivos como jugador clave votado.">
                    <h4>Insignia de Cooperación</h4>
                    <p>Completar 5 proyectos colectivos como jugador clave votado.</p>
                </div>
                
                <div class="achievement-card locked" title="Logro Bloqueado: Ser MVP en 2 competiciones distintas del Área Artística.">
                    <h4>Trofeo de Creatividad</h4> 
                    <p>Ser MVP en 2 competiciones distintas del Área Artística.</p>
                </div>

                <div class="achievement-card unlocked" title="Completar la carrera de resistencia en el tercio superior.">
                    <h4>Maratonista Novato</h4>
                    <p>Completar la carrera de resistencia en el tercio superior.</p>
                </div>

                <div class="achievement-card locked" title="Logro Bloqueado: Resolver un Reto de Codificación Avanzado con 100% de eficacia.">
                    <h4>Coder Junior</h4>
                    <p>Resolver un Reto de Codificación Avanzado con 100% de eficacia.</p>
                </div>

                <div class="achievement-card unlocked" title="Ganar el primer puesto en 3 debates consecutivos.">
                    <h4>Maestro Orador</h4>
                    <p>Ganar el primer puesto en 3 debates consecutivos.</p>
                </div>
                
                <div class="achievement-card locked" title="Logro Bloqueado: Diseñar y construir un circuito funcional en tiempo récord.">
                    <h4>Ingeniero de Circuitos</h4>
                    <p>Diseñar y construir un circuito funcional en tiempo récord.</p>
                </div>

            </div>
        </section>
    </main>
</body>
</html>
