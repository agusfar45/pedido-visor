# PedidoVisor: pedidos en tiempo real para una hamburguesería

Sistema que uso en **Boom Burger**, mi emprendimiento gastronómico, para reemplazar las comandas en papel.
El celular del mostrador carga el pedido y la pantalla de la cocina lo muestra **al instante**, sincronizados
con Firebase Realtime Database.

**Sitio:** https://agusfar45.github.io/pedido-visor/

## Cómo funciona

1. **Mostrador (celular):** se ingresa el número de pedido y cuántas hamburguesas lleva. Después, para cada
   una: variedad, simple o doble, aderezos y observaciones.
2. **Cocina (pantalla):** cada hamburguesa aparece arriba de la lista apenas se envía (`onChildAdded`), con
   letra grande para leerla de lejos.
3. Al marcar **✓ Listo**, el pedido se tacha, pasa al historial (`/historial`) y suma su precio al total vendido.
4. **Limpiar pantalla** borra de la base los pedidos ya despachados. El historial queda guardado.

```
celular ──push()──▶ Firebase /pedidos ──onChildAdded──▶ pantalla de cocina
                                                        └─ Listo ─▶ /historial + total del día
```

## Tecnologías

HTML, CSS y JavaScript sin frameworks · Firebase Realtime Database (SDK modular 10) · GitHub Pages

## Lo que mejoraría

Lo hice rápido para usarlo en el local. Hoy, con lo que aprendí de seguridad, cambiaría esto:

- **Reglas de seguridad de Firebase:** la base tiene que exigir autenticación para leer y escribir. Si no, cualquiera
  que conozca la URL puede cargar o borrar pedidos.
- **Inyección de HTML:** los pedidos se muestran con `innerHTML`, así que una observación con etiquetas HTML se
  interpretaría. Hay que usar `textContent`.
- Separar la vista del mostrador y la de la cocina en dos páginas, y sacar los precios del código para guardarlos
  en la base.

---

Tomás Agustín Farfán · Ingeniería en Informática (UCASAL) · [github.com/agusfar45](https://github.com/agusfar45)
