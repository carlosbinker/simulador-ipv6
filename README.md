# Simulador IPv6: SLAAC, DAD y NDP 🌐

## Descripción

Simulador interactivo para la **Cátedra de Redes** que permite visualizar y entender los tres procesos fundamentales de IPv6:

1. **SLAAC** (Stateless Address Autoconfiguration) - Autoconfiguración sin estado de direcciones IPv6
2. **DAD** (Duplicate Address Detection) - Detección de direcciones duplicadas
3. **NDP** (Neighbor Discovery Protocol) - Protocolo de descubrimiento de vecinos

## ✨ Funcionalidades

- 🎯 **Simulación de SLAAC múltiple**: Visualiza cómo cada PC obtiene direcciones IPv6 iniciando el proceso desde diferente fuente (RS desde A, B o C)
- 🔍 **Evaluación DAD dinámica**: Verifica que no existan direcciones duplicadas y genera Link-Local Addresses (LLA) para cada PC
- 📡 **Resolución NDP multi-flujo**: Simula 3 flujos diferentes de búsqueda de direcciones MAC: A→B, A→C, B→C
- 📊 **Inspector de Paquetes**: Captura y visualiza en tiempo real los detalles de cada capa de protocolo (Ethernet, IPv6, ICMPv6)
- 🎨 **Interfaz visual mejorada**: Representación gráfica de la topología de red con display de MACs, LLAs y GUAs en cada nodo
- 💾 **Neighbor Cache visual**: Panel derecho que muestra el estado del cache de descubrimiento de vecinos para cada PC

## 🏃 Uso

1. Abre `index.html` en tu navegador web
2. Usa los botones de control para ejecutar cada simulación:
   
   **SLAAC** (3 opciones - una por cada PC):
   - **SLAAC (RS de A)**: Autoconfiguración iniciada por PC-A
   - **SLAAC (RS de B)**: Autoconfiguración iniciada por PC-B
   - **SLAAC (RS de C)**: Autoconfiguración iniciada por PC-C
   
   **DAD** (3 opciones - verificación por PC):
   - **DAD PC-A**: Detección de dirección duplicada para PC-A (genera LLA)
   - **DAD PC-B**: Detección de dirección duplicada para PC-B (genera LLA)
   - **DAD PC-C**: Detección de dirección duplicada para PC-C (genera LLA)
   
   **NDP** (3 flujos de resolución):
   - **NDP A→B**: PC-A busca MAC de PC-B
   - **NDP A→C**: PC-A busca MAC de PC-C
   - **NDP B→C**: PC-B busca MAC de PC-C
   
   - **Reiniciar**: Limpia la simulación

3. Observa:
   - Las direcciones Link-Local (LLA) que aparecen cuando ejecutas DAD
   - Los paquetes capturados en el inspector
   - El cache de vecinos en el panel derecho

## 🔧 Tecnologías

- **HTML5** + **CSS3** - Interfaz y estilos
- **JavaScript Vanilla** - Lógica de simulación
- Sin dependencias externas

## 📚 Conceptos Cubiertos

### SLAAC
- Router Solicitation (ICMPv6 Type 133)
- Router Advertisement (ICMPv6 Type 134)
- Generación de dirección Global Unicast (GUA)
- Flags M/O en Router Advertisement

### DAD
- Neighbor Solicitation (ICMPv6 Type 135)
- Solicited-Node Multicast addresses
- Verificación de unicidad de direcciones

### NDP
- Neighbor Solicitation para resolución de direcciones
- Neighbor Advertisement con Source Link-Layer Address (SLLA)
- Target Link-Layer Address (TLLA)

## 📋 Topología

```
        ┌─────────────┐
        │     R1      │  Router IPv6
        │ 2001:db8:a::/64
        └─────└─┘─────┘
             │││
        ┌────┴┴┴────┐ Bus compartido (red compartida)
        │            │
     ┌──┴──┐      ┌──┴──┐
     │ PC-A│      │ PC-B│
     └─────┘      └─────┘
        │
     ┌──┴──┐
     │ PC-C│
     └─────┘
```

## 🎓 Información de Dispositivos

| Dispositivo | MAC Address | Dirección | Prefijo |
|-------------|-------------|-----------|---------|
| R1 (Router) | 00:AA:00:11:00:01 | fe80::2aa:ff:fe11:1 | 2001:db8:a::/64 |
| PC-A | 00:AA:00:22:00:0A | Autoconfigurada | - |
| PC-B | 00:AA:00:33:00:0B | Autoconfigurada | - |
| PC-C | 00:AA:00:44:00:0C | Autoconfigurada | - |

## 💡 Cómo Usar para Aprender

1. **Paso 1**: Ejecuta cualquiera de los botones "SLAAC" para ver cómo se distribuyen las direcciones IPv6 a todos los PC
2. **Paso 2**: Observa en el inspector los paquetes RS (Solicitud) y RA (Respuesta) intercambiados
3. **Paso 3**: Ejecuta los botones DAD (PC-A, PC-B, PC-C) para ver cómo se generan las Link-Local Addresses (LLA)
4. **Paso 4**: Verifica que las LLA aparezcan en cada nodo después de ejecutar DAD
5. **Paso 5**: Usa cualquiera de los botones NDP para entender cómo se resuelven las direcciones MAC entre dispositivos
6. **Paso 6**: Observa el panel "ARP Cache (Neighbor Discovery)" cómo se llena con las resoluciones
7. **Paso 7**: Reinicia y repite para consolidar los conceptos

## 🌍 Direcciones en Hexadecimal

El simulador utiliza direcciones IPv6 reales con el prefijo documentado `2001:db8::/32` (RFC 3849):

- **Link-Local Address (LLA)**: fe80::/10 (excepto para broadcast)
- **Global Unicast Address (GUA)**: 2001:db8:a:0:xxxx:xxxx:xxxx:xxxx
- **Solicited-Node Multicast**: ff02::1:xxxx:xxxx (últimos 24 bits de la IPv6)

## 📝 Notas Importantes

- Las direcciones Link-Local se generan automáticamente (fe80::)
- Las direcciones Global se derivan del MAC address usando EUI-64
- Las direcciones Multicast especiales (ff02::1, ff02::2) se usan para comunicación de grupo
- DAD es crítico antes de usar cualquier IPv6 nueva

## 🔗 Referencias

- [RFC 4862 - IPv6 Stateless Address Autoconfiguration](https://tools.ietf.org/html/rfc4862)
- [RFC 4861 - Neighbor Discovery for IPv6](https://tools.ietf.org/html/rfc4861)
- [RFC 3849 - IPv6 Documentation Address Prefix](https://tools.ietf.org/html/rfc3849)

---

**Desarrollo**: Cátedra de Redes  
**Última actualización**: 2026
