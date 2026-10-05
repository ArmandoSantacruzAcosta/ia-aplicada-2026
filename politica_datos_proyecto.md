digraph G {
  rankdir=LR;
  node [shape=box style="filled,rounded" fontname="Arial"];

  e1 [label="1. Captura\n\n• Reg. D1-D4, D7, D10\n• Resp: Propietario\n• Ctrl: HTTPS + Aviso" fillcolor="#1B365D" fontcolor=white];
  e2 [label="2. Almacenamiento\n\n• Guardado en BD Cloud\n• Resp: Custodio\n• Ctrl: AES-256 + MFA" fillcolor="#1B365D" fontcolor=white];
  e3 [label="3. Uso\n\n• Algoritmo Cotizador\n• Resp: Propietario\n• Ctrl: Logs + Rev. Humana" fillcolor="#1B365D" fontcolor=white];
  e4 [label="4. Compartición\n\n• Pago vía Pasarela\n• Resp: Administrador\n• Ctrl: PCI-DSS Token" fillcolor="#1B365D" fontcolor=white];
  e5 [label="5. Retención\n\n• Historial de Obra\n• Resp: Custodio\n• Ctrl: Max 24 meses" fillcolor="#1B365D" fontcolor=white];
  e6 [label="6. Eliminación\n\n• Borrado definitivo\n• Resp: Custodio\n• Ctrl: Sobrescritura" fillcolor="#1B365D" fontcolor=white];

  t1 [label="Proveedor Nube\n(AWS / GCP)" style="dashed,filled,rounded" fillcolor="#FFF3CD" color="#D99B00"];
  t2 [label="Pasarela Pagos\n(Stripe / MP)" style="dashed,filled,rounded" fillcolor="#FFF3CD" color="#D99B00"];

  e1 -> e2 [color=red penwidth=3 label="D7" fontcolor=red];
  e2 -> e3 [color=red penwidth=3 label="D7" fontcolor=red];
  e3 -> e4 [color=red penwidth=3 label="D7" fontcolor=red];
  e4 -> e5 [color=red penwidth=3 label="D7" fontcolor=red];
  e5 -> e6 [color=red penwidth=3 label="D7" fontcolor=red];

  e2 -> t1 [style=dashed color=gray];
  e4 -> t2 [style=dashed color=red penwidth=2];


## 1. Alcance
Esta política regula el tratamiento de los datos recolectados por la plataforma ConectaHogar AI. Cubre los identificadores de datos del cliente y arquitecto D1 (Nombre, Personal), D2 (Contacto, Personal), D3 (Currículum/Semblanza, Personal), D4 (Ubicación del terreno, Personal), D5 (Catálogo de materiales, No personal), D6 (Historial de cotización, Personal), D7 (Datos bancarios, Sensible), D8 (Celular, Personal), D9 (Foto perfil, Personal), D10 (Credenciales, Personal), D11 (Facturación, Personal), D12 (Portafolio, No personal), D13 (Cédula profesional, Personal), D14 (Reseñas, Personal), D15 (Presupuesto, Personal) y D16 (Topografía, No personal).

## 2. Ciclo de vida
El ciclo de vida abarca 6 etapas mapeadas en el diagrama oficial del proyecto: Captura (a cargo del Propietario del dato), Almacenamiento (a cargo del Custodio de la información), Uso (a cargo del Propietario y Administrador del Sistema), Compartición (a cargo del Administrador del Sistema con proveedores externos), Retención (a cargo del Custodio) y Eliminación (a cargo del Custodio de la información).

## 3. Normativa aplicable
El proyecto cumple con la Ley Federal de Protección de Datos Personales en Posesión de los Particulares (LFPDPPP - México, publicada en DOF el 20 de marzo de 2025) bajo la supervisión de la Secretaría Anticorrupción y Buen Gobierno. Se adoptan como referencias internacionales la Ley de IA de la Unión Europea (Reglamento UE 2024/1689) y las funciones del marco voluntario NIST AI RMF 1.0.

## 4. Controles comprometidos
La plataforma compromete los siguientes controles operativos: obtención de consentimiento informado previo (Propietario del dato), cifrado de base de datos AES-256 (Custodio), tokenización de transacciones bancarias (Administrador del sistema), opción de revisión humana de presupuestos de IA (Administrador del sistema), auditabilidad de accesos (Custodio) y borrado definitivo de registros tras 24 meses de inactividad (Custodio).

## 5. Manejo de datos con herramientas de IA
Queda estrictamente prohibido ingresar datos identificables o sensibles (D1, D2, D4, D7, D10, D11) a modelos generativos públicos como ChatGPT, Gemini o Deepseek. Únicamente se podrán enviar a APIs de IA datos técnicos o anonimizados (D5, D12, D16) o escenarios ficticios para la simulación de presupuestos y estilos arquitectónicos.

## 6. Revisión
Esta política de datos se revisará de manera obligatoria cada seis (6) meses o inmediatamente tras cualquier cambio estructural en la arquitectura de la app. Su aprobación y modificación corresponden al Líder del Proyecto y al Oficial de Ciberseguridad de la organización.
