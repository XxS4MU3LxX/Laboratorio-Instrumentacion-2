## Laboratorio 2 Medicion continua del estres
# **Integrantes**
>
* María Angélica Vargas Saldaña 5600820
* Samuel Esteban Fonseca Luna 5600808
* Laura Daniela Triana Molano 5600

<h2 align="center">𝙞𝙣𝙩𝙧𝙤𝙙𝙪𝙘𝙘𝙞ó𝙣</h2>

La actividad electrodérmica o EDA (Electrodermal Activity) comprende todos aquellos fenómenos eléctricos que ocurren a nivel de la piel, incluyendo los cambios en su capacidad para conducir la electricidad, conocida como conductancia cutánea [1]. Esta propiedad está estrechamente ligada a la secreción de las glándulas sudoríparas ecrinas, las cuales se encuentran inervadas exclusivamente por el sistema nervioso simpático [17].

La señal de conductancia cutánea se compone de dos elementos fundamentales [18, 365]:

Componente Tónica (SCL - Skin Conductance Level): Representa el nivel basal o de reposo de la señal, caracterizado por cambios lentos en el tiempo (de segundos a minutos), asociados al nivel general de activación fisiológica.
Componente Fásica (SCR/GSR - Skin Conductance Response): Representa las respuestas rápidas, dinámicas y transitorias ante estímulos específicos emocionales, cognitivos o sensoriales. Se manifiesta como un incremento súbito seguido de una recuperación paulatina que toma un tiempo considerablemente mayor.

<h2 align="center">𝙤𝙗𝙟𝙚𝙩𝙞𝙫𝙤𝙨</h2>

𝙊𝙗𝙟𝙚𝙩𝙞𝙫ο 𝙜𝙚𝙣𝙚𝙧𝙖𝙡:

Proporcionar un sistema de medición continua de estrés basado en la respuesta galvánica cutánea (GSR) [20].

𝙊𝙗𝙟𝙚𝙩𝙞𝙫ο𝙨 𝙀𝙨𝙥𝙚𝙘𝙞́𝙛𝙞𝙘ο𝙨:

• Identificar y diferenciar experimentalmente las componentes tónica (SCL) y fásica (GSR) de la respuesta galvánica cutánea [20].

• Elaborar un dispositivo vestible de bajo costo que permita capturar de forma continua las variaciones de la GSR [20].

• Plantear hipótesis desde la fisiología humana sobre el rol de la GSR como indicador de estrés [20].

𝙎𝙚𝙣𝙨ο𝙧
El sensor de GSR (Galvanic Skin Response) funciona aplicando una pequeña diferencia de potencial constante a través de dos electrodos colocados en contacto con la piel [63, 240]. Para esta práctica, el dispositivo vestible se diseñó en formato de manilla (wristband) colocada en la muñeca del participante [26], empleando electrodos caseros de aluminio para registrar las variaciones de conductancia cutánea.

𝘾𝙤𝙣𝙨𝙚𝙣𝙩𝙞𝙢𝙞𝙚𝙣𝙩𝙤 𝙞𝙣𝙛ο𝙧𝙢𝙖𝙙𝙤 𝙙𝙚𝙡 𝙥𝙖𝙧𝙩𝙞𝙘𝙞𝙥𝙖𝙣𝙩𝙚
Debido a que la práctica involucró la adquisición de datos fisiológicos mediante el registro de señales de conductancia cutánea en un sujeto de prueba humano sano [24], se diseñó e implementó un formato de Consentimiento Informado. En este documento se explicó de forma clara y explícita al participante el propósito académico de la práctica, el carácter seguro e inocuo del procedimiento (no invasivo), la confidencialidad de la información y la voluntariedad de su participación, cumpliendo con los principios bioéticos y de seguridad para el registro de biopotenciales y variables fisiológicas humanas.

<img width="203" height="257" alt="image" src="https://github.com/user-attachments/assets/a9ca0362-32fa-4c8e-81f1-65df34fb6aa8" />

𝙈ο𝙣𝙩𝙖𝙟𝙚 𝙚𝙭𝙥𝙚𝙧𝙞𝙢𝙚𝙣𝙩𝙖𝙡
El montaje del dispositivo vestible de adquisición se compone de:

Electrodos y Sujeción: Dos electrodos caseros de aluminio montados de forma interna sobre una manilla, asegurando una sujeción firme sobre la muñeca del participante para garantizar el contacto mecánico constante con la piel.
Circuito de Acondicionamiento (Divisor de Tensión): Un circuito pasivo compuesto por una resistencia de referencia de R1 = 68 kΩ conectada en serie con la resistencia cutánea del sujeto, y un condensador de C1 = 1 µF en paralelo para el filtrado analógico de ruido electromagnético de alta frecuencia [23].
Tarjeta de Adquisición y Procesamiento: Módulo de desarrollo ESP32, el cual realiza la digitalización de la señal analógica acondicionada a través de su convertidor analógico-digital (ADC) de 12 bits (pin ADC0).
Cálculos de Seguridad Eléctrica: Para garantizar la integridad física del sujeto y cumplir con la norma internacional de seguridad, se diseñó el circuito de modo que la corriente máxima que circule por la piel del participante nunca supere el límite de 1 mA, incluso ante un cortocircuito absoluto en los electrodos ($R_{skin} = 0\text{ }\Omega$) [25]. Dado que el ESP32 trabaja con un nivel de tensión lógica de 3.3 VDC, el cálculo de corriente máxima es: $$I_{max} = \frac{V_{CC}}{R_1 + R_{skin}} = \frac{3.3\text{ V}}{68\text{ k}\Omega + 0\text{ }\Omega} \approx 0.0485\text{ mA} = 48.5\text{ }\mu\text{A}$$ De acuerdo con la norma IEC 60479 (Tabla 1), el umbral de percepción humana para corriente continua inicia entre 0 y 4 mA [248]. Dado que $48.5\text{ }\mu\text{A} \ll 1\text{ mA}$, se certifica que el circuito es completamente seguro e imperceptible para el participante [249, 254].

# Resultados
*VENTAJAS*

Ergonomía y Portabilidad: El formato de manilla es sumamente cómodo y ergonómico, permitiendo que el usuario mueva libremente la mano y realice tareas cotidianas sin la restricción mecánica que imponen los electrodos de velcro tradicionales en las yemas de los dedos.
Inalámbrico Integrado: Al utilizar el microcontrolador ESP32, se aprovecha su conectividad Bluetooth nativa sin necesidad de añadir módulos transceptores externos adicionales, lo que reduce el tamaño, peso y consumo del dispositivo vestible.
Alta Resolución de Digitalización: El ADC de 12 bits del ESP32 ofrece 4096 niveles de cuantización (en comparación con los 1024 niveles de un microcontrolador tradicional de 10 bits), permitiendo detectar variaciones de voltaje sumamente sutiles debidas a picos fásicos atenuados.

*DESVENTAJAS*

Pasivación y Ruido del Aluminio: El aluminio es un metal altamente reactivo y polarizable. Al contacto con el sudor (electrolito rico en NaCl), sufre un rápido proceso de oxidación que genera una capa pasivante de óxido de aluminio ($Al_2O_3$). Esto altera dinámicamente la impedancia de contacto, introduciendo un fuerte ruido de deriva basal (drift) en la señal.
Menor Sensibilidad Fisiológica: La muñeca posee una densidad significativamente menor de glándulas sudoríparas ecrinas en comparación con las falanges distales de los dedos. Esto causa que las respuestas fásicas (SCR) tengan una amplitud fisiológica mucho más pequeña y difícil de registrar.
No Linealidad del ADC del ESP32: El convertidor analógico-digital del ESP32 presenta una marcada no-linealidad en los extremos de su rango dinámico (cerca de 0 V y de 3.3 V), requiriendo de algoritmos de calibración y mapeo por software para evitar distorsiones en las lecturas de conductancia.
En esta etapa, el dispositivo fue configurado para capturar la señal GSR del sujeto de prueba en reposo y bajo una maniobra de estimulación controlada para establecer los umbrales fisiológicos de estrés [26, 27].

Prueba de Reposo e Inspiración Profunda: El sujeto de prueba se ubicó cómodamente sentado y en silencio. Tras registrar una línea base estable (SCL), se le solicitó realizar una inspiración profunda seguida de una exhalación lenta. Como respuesta fisiológica inmediata, la señal GSR experimentó un incremento rápido y marcado en su conductancia fásica (SCR) antes de retornar lentamente a su valor inicial [27, 364].
Definición de Umbrales de Estrés: A partir de las diferencias registradas entre el nivel basal ($SC_{min}$) y el pico máximo alcanzado durante la estimulación ($SC_{max}$), denotadas como la amplitud de la respuesta $\Delta SC = SC_{max} - SC_{min}$ [18], se definieron experimentalmente tres umbrales de estimación adaptados a la atenuación de señal en la muñeca:
Poco Estrés (Estado Basal/Relajación): $\Delta SC < 0.05\text{ }\mu\text{S}$. Ausencia de picos de respuesta galvánica significativos y línea base tónica estable.
Estrés Moderado (Activación Leve): $0.05\text{ }\mu\text{S} \le \Delta SC \le 0.2\text{ }\mu\text{S}$. Ocurrencia de pequeñas fluctuaciones fásicas ante estímulos transitorios o de atención.
Estrés Elevado (Activación Simpática Alta): $\Delta SC > 0.2\text{ }\mu\text{S}$. Presencia de picos fásicos de gran amplitud, alta frecuencia de ráfagas e incremento notable de la conductancia basal (SCL).
Adaptación para Transmisión Inalámbrica: Se programó el hardware del ESP32 habilitando la transmisión a través de Bluetooth (configurando un perfil de emulación de puerto serie clásico o BLE). La trama de datos de conductancia y la clasificación del nivel de estrés se enviaron inalámbricamente a un dispositivo celular, empleando la aplicación de diagnóstico nRF Connect para capturar, visualizar y registrar de forma portátil los datos fisiológicos en tiempo real [27, 28].
En la fase final de la práctica, se validó el funcionamiento del dispositivo vestible de manilla durante un protocolo experimental de estrés cognitivo [28].

Se le aplicó al sujeto de prueba un breve examen de alta demanda mental contrarreloj (resolución rápida de problemas matemáticos bajo presión de tiempo). Durante el transcurso de la prueba, la manilla transmitió de forma inalámbrica los niveles de estrés hacia el celular del operador.

Hallazgos y Discusión Fisiológica: Al iniciar las preguntas del examen, se observó un incremento drástico y sostenido en la señal de conductancia cutánea. Esto se debe a que la carga cognitiva y el estado de alerta activan la corteza prefrontal y el sistema límbico, estructuras que estimulan al hipotálamo para disparar impulsos a través de las fibras postganglionares sudomotoras simpáticas hacia las glándulas sudoríparas [242]. El aumento inmediato de la micro-sudoración en la muñeca disminuyó la resistencia eléctrica de contacto (aumento de la conductancia), disparando alertas continuas de Estrés Elevado en la aplicación nRF Connect del celular. Una vez finalizado el examen y tras entrar en el periodo de recuperación, la conductancia basal disminuyó paulatinamente en concordancia con el retorno a la homeostasis simpato-vagal.

𝟭. El dispositivo vestible en formato de manilla basado en el microcontrolador ESP32 demostró una alta sensibilidad y rapidez para capturar las respuestas del sistema nervioso simpático ante estímulos cognitivos y físicos, clasificando de forma automática el nivel de estrés del usuario en tiempo real [30, 242].

𝟮. La integración de la resistencia de protección de $68\text{ k}\Omega$ limitó físicamente la corriente que circula por el usuario a un máximo seguro e imperceptible de $48.5\text{ }\mu\text{A}$ (trabajando a 3.3V), lo que garantiza el cumplimiento estricto de la norma de seguridad eléctrica IEC 60479 [25, 248].

𝟯. El uso de electrodos caseros de aluminio en la muñeca demostró ser viable para la captura de variaciones basales, pero evidenció limitaciones críticas como la rápida deriva basal (drift) por oxidación galvánica y una menor densidad de señal en comparación con los dedos. Esto resalta la importancia de la selección de materiales en la interfaz electrodo-piel (como electrodos húmedos de Ag/AgCl) para aplicaciones que requieran una alta confiabilidad diagnóstica en entornos cotidianos [82, 365].

𝘽𝙞𝙗𝙡𝙞𝙤𝙜𝙧𝙖𝙛𝙞𝙖

+ W. Boucsein, Electrodermal Activity. Nueva York, NY, Estados Unidos: Springer Science & Business Media, 2012.
+ M. L. Loggia, M. Juneau y C. M. Bushnell, “Autonomic responses to heat pain: Heart rate, skin conductance, and their relation to verbal ratings and stimulus intensity,” Pain, vol. 152, no. 3, pp. 592–598, 2011. https://doi.org/10.1016/j.pain.2010.11.032.
+ M. Breimhorst, S. Sandrock, M. Fechir, N. Hausenblas, C. Geber y F. Birklein, “Do intensity ratings and skin conductance responses reliably discriminate between different stimulus intensities in experimentally induced pain?” The Journal of Pain, vol. 12, no. 1, pp. 61–70, 2011. https://doi.org/10.1016/j.jpain.2010.04.012.
+ B. Figner y R. O. Murphy, “Using skin conductance in judgment and decision making research,” en A Handbook of Process Tracing Methods for Decision Research, M. Schulte-Mecklenbeck, A. Kuehberger y R. Ranyard, Eds. Nueva York, NY, Estados Unidos: Psychology Press, 2011, pp. 163–184.
