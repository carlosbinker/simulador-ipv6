# Simulador IPv6: SLAAC, DAD y NDP 🌐

## Descripción

Simulador interactivo para la **Cátedra de Redes** que permite visualizar y entender los tres procesos fundamentales de IPv6:

1. **SLAAC** (Stateless Address Autoconfiguration) - Autoconfiguración sin estado de direcciones IPv6
2. **DAD** (Duplicate Address Detection) - Detección de direcciones duplicadas
3. **NDP** (Neighbor Discovery Protocol) - Protocolo de descubrimiento de vecinos

## ✨ Funcionalidades

- 🎯 **Simulación de SLAAC**: Visualiza cómo los dispositivos obtienen direcciones IPv6 a través de Router Solicitation (RS) y Router Advertisement (RA)
- 🔍 **Evaluación DAD**: Verifica que no existan direcciones duplicadas antes de adoptar una dirección IPv6
- 📡 **Resolución NDP**: Simula la búsqueda de direcciones MAC entre dispositivos usando Neighbor Solicitation (NS) y Neighbor Advertisement (NA)
- 📊 **Inspector de Paquetes**: Captura y visualiza en tiempo real los detalles de cada capa de protocolo
- 🎨 **Interfaz visual**: Representación gráfica de la topología de red con bus vertical

## 🏃 Uso

1. Abre `index.html` en tu navegador web
2. Usa los botones de control para ejecutar cada simulación:
   - **1. SLAAC**: Inicia la autoconfiguración de direcciones IPv6
   - **DAD PC-A/B/C**: Ejecuta la detección de direcciones duplicadas para cada PC
   - **2. NDP**: Simula la resolución de direcciones (PC-A busca a PC-B)
   - **Reiniciar**: Limpia la simulación

3. Observa los paquetes capturados en el inspector inferior

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

1. **Paso 1**: Ejecuta el botón "SLAAC" para ver cómo se distribuyen las direcciones IPv6
2. **Paso 2**: Observa en el inspector los paquetes RS y RA intercambiados
3. **Paso 3**: Prueba los botones DAD para ver cómo se verifica cada dirección
4. **Paso 4**: Usa NDP para entender cómo se resuelven las direcciones MAC entre los dispositivos
5. **Paso 5**: Reinicia y repite para consolidar los conceptos

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
