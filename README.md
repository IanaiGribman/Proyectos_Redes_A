# Redes de Computadoras · Ejercicios y simuladores

Colección de páginas web educativas para estudiar la materia **Redes de Computadoras** (enlace y red, con Tanenbaum como bibliografía de referencia). Cada página es un único archivo HTML: se descarga, se abre con doble click y funciona, sin servidor ni instalación.

## Cómo usarlo

Abrí [`index.html`](index.html) en el navegador. Es la portada: lista todas las páginas y tiene de fondo una animación de paquetes viajando entre routers. Cada página tiene un botón **← Inicio** para volver.

## Páginas

| Archivo | Qué es |
|---|---|
| [`index.html`](index.html) | Portada con el listado de páginas. |
| [`simulador_protocolos_ip.html`](simulador_protocolos_ip.html) | Simulador paso a paso de los protocolos complementarios a IP: **ARP, RARP, BOOTP, DHCP e ICMP**, con examen propio. |
| [`examenes_parciales.html`](examenes_parciales.html) | Exámenes de parcial en opción múltiple (teoría y práctica), con corrección al final o al responder. |
| [`simulador_switches.html`](simulador_switches.html) | Simulador de redes Ethernet: topologías con hosts, switches y hubs, aprendizaje de MAC y modo práctica. |
| [`practica_ip.html`](practica_ip.html) | Práctica de IPv4: examen avanzado de 6 preguntas. |

### Simulador de protocolos IP

Una red de práctica con tres LAN y dos routers. Cada escenario se recorre paso a paso, con animación, cabeceras de cada trama y el estado de las cachés ARP:

1. **Viaje del paquete**: cómo un datagrama cruza routers y cómo cada salto resuelve su MAC con ARP (la IP no cambia, las MAC y el TTL sí).
2. **ARP**: resolución normal, IP inexistente, ARP gratuito y proxy ARP.
3. **RARP**: con el servidor en la misma LAN, en otra LAN, o con la MAC sin registrar.
4. **BOOTP**: BOOTREQUEST/BOOTREPLY, relay y descarga por TFTP.
5. **DHCP**: DISCOVER, OFFER, REQUEST y ACK, con relay y renovación.
6. **ICMP**: ping, traceroute, TTL expirado, host inexistente y red sin ruta.
7. **Resumen y repaso**, y 8. **Examen** con preguntas fijas y otras generadas con el propio motor de la simulación.

### Exámenes de parcial

Incluye cuatro modelos precargados. Las preguntas de teoría admiten varias opciones correctas (puntaje: `puntos × (correctas − incorrectas marcadas) / total de correctas`, mínimo 0) y los ejercicios prácticos se responden por opción múltiple.

Algunas preguntas tienen soporte gráfico: **diagramas de switches y hubs** (la página simula el aprendizaje de MAC y el reenvío, genera las opciones y, tras corregir, muestra la simulación trama por trama), **tablas** y **topologías de routers**.

#### Cargar tus propios exámenes

Desde la página, en «Cargar otro JSON de exámenes», se puede subir o pegar un JSON con el mismo formato. Ahí mismo hay un botón **Copiar instrucciones** con la descripción completa del formato, pensada para pasársela a un agente que genere el JSON. Resumen:

```jsonc
{
  "examenes": [{
    "id": "modelo-1",
    "titulo": "Parcial modelo 1",
    "t": [                       // teoría
      { "e": "Enunciado", "o": [["Opción", 1, "Justificación"], ["Otra", 0, "Justificación"]] },
      { "e": "Contexto", "g": { /* red de switches */ }, "ask": { "k": "hosts", "n": 2 } }
    ],
    "p": [                       // práctica
      { "titulo": "…", "e": "…", "pts": 15, "c": [["a) Etiqueta", "respuesta", "alternativa"]], "j": "Resolución" }
    ]
  }]
}
```

Claves opcionales: `g` + `ask` (preguntas gráficas de switches), `tb` (tablas), `rd` (topología de routers y redes), `d` (distractores a mano para respuestas de texto) y `ptsT` (puntos totales de teoría; 50 por defecto, repartidos en partes iguales).

## Agregar una página nueva

1. Poné el archivo `.html` en la raíz del repo.
2. En [`index.html`](index.html), copiá uno de los bloques `<a class="page">` del listado y cambiá `href`, título y descripción.
3. (Opcional) Agregá un enlace `<a href="index.html">← Inicio</a>` en la página nueva.

## Notas técnicas

- Todo es HTML, CSS y JavaScript en un solo archivo por página, sin dependencias ni paso de compilación. La excepción es `practica_ip.html`, que carga Bootstrap y otros recursos desde una CDN y por eso necesita conexión a internet.
- El simulador de Ethernet guarda tu configuración automáticamente en el navegador.
- La portada y el simulador de protocolos respetan la preferencia del sistema de *reducir movimiento*.
- Las direcciones IP y MAC de los ejemplos son ficticias.

## Bibliografía

- A. S. Tanenbaum y D. J. Wetherall, *Redes de computadoras*: capa de enlace, Ethernet y capa de red (protocolos de control de Internet).
- RFC 826 (ARP), RFC 903 (RARP), RFC 951 (BOOTP), RFC 792 (ICMP), RFC 2131 (DHCP).
- Unos pibes de la facu: Ianai Gribman y Dante Emilio Gregorini.
