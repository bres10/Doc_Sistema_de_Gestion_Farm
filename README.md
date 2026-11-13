# Sistema de Gestión Farmacéutica

Plataforma web para administrar la operación de una red de farmacias: sucursales, catálogo de medicamentos, inventario por ubicación, cajas, ventas, pedidos, usuarios y trazabilidad operativa.

## Descripción

El sistema centraliza las operaciones diarias de una farmacia y permite controlar el flujo desde la existencia de un medicamento en una sucursal hasta su venta y registro financiero.

La aplicación está diseñada para crecer hacia módulos de transferencias entre sucursales, activos, auditoría, entregas y atención de pedidos desde call center.

## Funcionalidades

### Operación actual

- Autenticación de usuarios con Supabase Auth.
- Gestión de usuarios, roles, sucursales y estados de cuenta.
- Catálogo de medicamentos con SKU, precios y datos operativos.
- Inventario por sucursal, lote y fecha de vencimiento.
- Alta de existencias desde una sucursal específica.
- Filtros de inventario por sucursal y medicamento.
- Apertura y consulta del historial de cajas.
- Edición y cierre de cajas con monto inicial y monto final.
- Creación de ventas y pedidos.
- Validación de caja abierta antes de vender.
- Validación de existencias disponibles por sucursal.
- Descuento transaccional de inventario al confirmar una venta.
- Registro automático del ingreso en caja.
- Historial de pedidos y referencias operativas.

### Evolución prevista

- Transferencias entre sucursales con solicitud, despacho, tránsito y recepción.
- Reversiones y devoluciones con movimientos compensatorios.
- Auditoría detallada de cambios y acciones administrativas.
- Activos fijos y control patrimonial.
- Entregas y asignación de pedidos.
- Integración con portal de clientes y call center.

## Flujo principal de venta

1. Abrir una caja para la sucursal correspondiente.
2. Seleccionar la sucursal en **Ventas y pedidos**.
3. Elegir una caja abierta.
4. Registrar los datos del cliente.
5. Agregar medicamentos y cantidades disponibles.
6. Seleccionar el método de pago.
7. Confirmar la venta.
8. El sistema valida el stock y ejecuta la operación de forma transaccional.
9. Se descuenta el inventario.
10. Se registra el movimiento de salida y el ingreso en caja.

Si no existe inventario suficiente en la sucursal seleccionada, la venta se rechaza sin aplicar cambios parciales.

## Arquitectura

- **Frontend:** Next.js 16, React 19 y App Router.
- **Lenguaje:** TypeScript.
- **Estilos:** Tailwind CSS 4 y componentes reutilizables.
- **Iconos:** Lucide React.
- **Backend y autenticación:** Supabase.
- **Base de datos:** PostgreSQL administrado por Supabase.
- **Autorización:** roles y políticas Row Level Security (RLS).
- **Operaciones críticas:** Server Actions y funciones RPC transaccionales.
- **Despliegue recomendado:** Vercel.

## Requisitos

- Node.js 20 o superior.
- pnpm, npm o yarn.
- Un proyecto de Supabase configurado.
- Variables de entorno disponibles para la aplicación.


## Seguridad y control de datos

- Las operaciones administrativas requieren autenticación y roles autorizados.
- Las operaciones financieras y de inventario se ejecutan en el servidor.
- Las operaciones de venta validan la sucursal, caja, existencias y cantidades antes de confirmar.
- La base de datos utiliza RLS para proteger el acceso a las tablas expuestas.
- Las operaciones sensibles conservan referencias para facilitar la trazabilidad.
- Las ventas no deben modificar saldos directamente: cada cambio debe registrarse mediante movimientos.
- Las claves privadas de Supabase no deben enviarse al cliente.

## Estructura relevante

```text
app/
├── (auth)/              # Inicio de sesión y recuperación de acceso
├── (dashboard)/         # Módulos protegidos de la aplicación
│   ├── dashboard/       # Resumen operativo
│   ├── inventory/       # Inventario por sucursal
│   ├── sales/           # Ventas y pedidos
│   ├── cash/            # Apertura, historial y cierre de cajas
│   ├── users/           # Administración de usuarios
│   └── ...
components/              # Componentes visuales reutilizables
lib/
├── data/operations.ts   # Consultas y acciones server-side
└── supabase/            # Clientes de Supabase
```

## Estado del proyecto

El proyecto se encuentra en desarrollo activo. El flujo base de venta ya conecta pedidos, inventario y caja. Las funcionalidades futuras se incorporarán de forma incremental, priorizando consistencia financiera, trazabilidad y permisos por rol.

## Licencia

La licencia del proyecto debe definirse antes de distribuirlo públicamente. Mientras no exista una declaración explícita, todos los derechos sobre el código quedan reservados a su autor.

## Contacto y presentación

Para presentar el sistema, revisa primero la configuración de Supabase, crea un usuario administrador y prepara datos de demostración por sucursal. No incluyas credenciales, claves privadas ni información real de pacientes o clientes en capturas, issues o documentación pública.

---

Desarrollado con Next.js, React, TypeScript, Supabase y Vercel.
