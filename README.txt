🏎️ OBDII Telemetry Analyzer, del escáner OBDII de mi coche a un Dashboard interactivo de Telemetría 📊

Aplicando el análisis de datos a problemas del día a día! 

Compre un escáner OBDII ELM327 de 9€ para analizar la salud del motor de mi coche, es un motor turbo (que suelen traer problemas). 
Si bien tengo pocos conocimientos de mecánica me encontré con que la APP oficial asociada al escáner mostraba información muy pobre 
para el correcto análisis, interpretación y diagnóstico. 
Entonces ante la necesidad del análisis de datos para la toma de decisiones, acepte el desafío, me puse manos a la obra y terminé 
construyendo una Web App interactiva con un dashboard, a la cual se le sube el fichero CSV del escáner y como resultado nos muestra 
las graficas, datos clave, interpretación de la información por una IA y el informe descargable en PDF.

Cuando descargué los datos en CSV de mi sesión de conducción del escáner OBDII, me encontré con dos problemas:

1. Las marcas de tiempo estaban en segundos puros en lugar de un formato legible `HH:MM:SS`.

2. Los valores numéricos venían corruptos por la codificación de la app del escáner.

¿Qué haces cuando tus datos de origen están completamente corruptos? Limpiarlos y construir un Dashboard!📊

🛠️ Para solucionarlo, diseñé un analizador web completo que:
✅ Automatiza la limpieza y normalización del CSV.
✅ Correlaciona la demanda del conductor (Pedal D) con la respuesta del motor (RPM) y la potencia generada (Power from MAF).
✅ Mide la eficiencia del turbocompresor (Sobrealimentación vs Presión MAP).
✅ Genera un reporte diagnóstico automático listo para exportar.


📊 **KPIs generados**
1-KPIs de Rendimiento del Motor y Transmisión
✅ RPM Maximum / Peak Engine Speed: Régimen máximo alcanzado durante la prueba (pico de 3,450 RPM).
✅ RPM Idle / Engine Idle Speed: Régimen medio en ralentí (promedio de 890 RPM).
✅ Pedal Acelerador Position Max (%): Porcentaje máximo de apertura/presión del acelerador (82.35% o 82.4% de carga pedida).
✅ Potencia Estimada (Power from MAF) (HP): Potencia máxima calculada a partir de la masa de aire que entra por la admisión (pico de 52.6 HP).

2-KPIs de Gestión del Turbo y Presión de Admisión
✅ Peak Boost Pressure (PSI / bar): Sobrealimentación / Presión relativa máxima entregada por el turbo por encima de la atmosférica (pico de +14.2 PSI / 0.98 bar).
✅ Minimum Intake Pressure / Idle Vacuum (PSI / kPa): Presión absoluta mínima en el colector con mariposa cerrada / ralentí (3.75 PSI abs / 25.8 kPa abs).
✅ Calculated Boost in Vacuum (PSI): Depresión máxima registrada en desaceleración o ralentí (-10.94 PSI). 

3-KPIs de Eficiencia de Flujo de Aire (MAF) y Admisión
✅ Maximum Mass Air Flow (g/s): Caudal máximo de aire aspirado registrado por el sensor MAF (43.83 g/s).
✅ Idle Mass Air Flow (g/s): Caudal de aire en ralentí (1.43 g/s).
✅ Air-to-Power Ratio (HP per g/s): Ratio de conversión de caudal de aire en potencia estimada 1.20 HP / g/s.

💡 **Insights extraídos:**
• Detección de respuesta lineal del motor: Rampa perfecta de pedal acelerador (18.8% → 82.4%) con escalado de RPMs (890 → 3,450 RPM).
• Salud del Turbo & MAF: Transición limpia de vacío (-11 PSI) a carga positiva de sobrealimentación (+14.2 PSI) manteniendo una constante perfecta de 1.2 HP / (g/s) de aire.
• Hallazgo: Registrar un vacío de 3.75 PSI abs (-10.94 PSI de boost) a 890 RPM descarta de plano cualquier fuga de aire en el colector de admisión posterior a la mariposa
• Diagnóstico Turbo: Activación efectiva del sistema de sobrealimentación en rango de carga.



La analítica de datos no trata solo de trabajar con bases de datos limpias en SQL, sino de saber tomar datos 'sucios' del mundo real y convertirlos en decisiones visuales e inteligibles.
