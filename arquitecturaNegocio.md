# ARQUITECTURA DEL NEGOCIO
## Cadena de Farmacias - Modelo Operativo

### 1. Introducción

#### 1.1 Propósito
Definir la arquitectura del negocio de la cadena de farmacias, incluyendo 
procesos, actores, sistemas y su interrelación con el Sistema de Gestión 
Farmacéutica (SGF).

#### 1.2 Alcance
Cubre la estructura organizacional, procesos de negocio, sistemas de 
información y tecnología que soportan la operación de la cadena.

#### 1.3 Definiciones
| Término | Definición |
|---------|------------|
| SGF | Sistema de Gestión Farmacéutica |
| BPMN | Business Process Model and Notation |
| RLS | Row Level Security |
| RPC | Remote Procedure Call |
| IPO | Oferta Pública Inicial |

### 2. Estructura Organizacional

La cadena de farmacias se organiza en cuatro niveles jerárquicos:

**Nivel 1 - Dirección Estratégica**
- Junta Directiva (Inversionistas)
- Gerencia General (CEO)

**Nivel 2 - Gerencias Corporativas**
- Gerencia de Operaciones
- Gerencia de Finanzas
- Gerencia de Tecnología

**Nivel 3 - Supervisión Regional**
- Gerentes Regionales
- Auditoría Interna
- Desarrollo y Soporte

**Nivel 4 - Operación Local**
- Gerentes de Sucursal
- Cajeros y Bodegueros

<img width="1291" height="533" alt="image" src="https://github.com/user-attachments/assets/c33d7741-78ba-4131-b0e3-672c5961642e" />

### 3. Procesos de Negocio

#### 3.1 Proceso de Venta
1. Cliente solicita medicamento
2. Consulta de medicamento en catálogo
3. Validación de stock y caja abierta
4. Registro de venta
5. Confirmación de venta
6. Descuento de inventario
7. Registro de ingreso en caja
8. Preparación de pedido
9. Entrega de producto
10. Cliente recibe

#### 3.2 Proceso de Transferencia
1. Sucursal origen solicita transferencia
2. Aprobación de solicitud
3. Despacho de medicamentos
4. Tránsito entre sucursales
5. Recepción en sucursal destino
6. Actualización de inventario en ambas sucursales
7. Registro de movimientos

#### 3.3 Proceso de Pedido por Call Center (futuro)
1. Cliente llama a call center
2. Operador toma pedido
3. Consulta de stock en sucursales cercanas
4. Verificación de tiempo de entrega
5. Información al cliente (disponibilidad, pago, tiempo)
6. Confirmación de pedido
7. Asignación de sucursal óptima
8. Entrega de pedido
9. Cliente recibe

#### 3.4 Proceso de Auditoría
1. Selección de sucursal a auditar
2. Consulta de movimientos de inventario
3. Consulta de movimientos de caja
4. Verificación de activos fijos
5. Revisión de planilla y gastos
6. Generación de reporte
7. Acciones correctivas

<img width="1402" height="449" alt="image" src="https://github.com/user-attachments/assets/e90f4f82-2e7d-4dc5-b800-bc7c75a1583c" />

### 4. Sistemas de Información

#### 4.1 Capas de la Arquitectura

**Capa de Presentación**
- Portal Cliente (futuro)
- Panel Administrativo
- App Móvil (futuro)
- Call Center (futuro)

**Capa de Aplicación**
- Módulo de Inventario
- Módulo de Ventas
- Módulo de Cajas
- Módulo de Usuarios
- Módulo de Transferencias
- Módulo de Activos
- Módulo de Auditoría
- Módulo de Reportes

**Capa de Datos**
- PostgreSQL (Supabase)
- Tablas: inventory, medicines, sales, cash, transfers, assets, users, audit

**Capa de Infraestructura**
- Vercel (Hosting)
- Supabase (DB/API)
- CDN
- Auth

#### 4.2 Integraciones

| Sistema | Tipo | Propósito |
|---------|------|-----------|
| Supabase Auth | Interno | Autenticación |
| Supabase DB | Interno | Persistencia |
| Vercel | Interno | Hosting |
| Call Center | Futuro | Pedidos telefónicos |
| Portal Cliente | Futuro | Pedidos web |
| Pasarela Pago | Futuro | Pagos en línea |
| ERP Contable | Futuro | Contabilidad |

<img width="880" height="681" alt="image" src="https://github.com/user-attachments/assets/5ca52083-5574-4348-bccb-100a0b36451e" />

### 5. Modelo de Datos (Alto Nivel)

#### 5.1 Entidades Principales
- Sucursales: Puntos de venta
- Medicamentos: Catálogo
- Inventario: Stock por sucursal
- Movimientos: Trazabilidad
- Ventas: Transacciones
- Cajas: Control de efectivo
- Usuarios: Personal
- Roles: Permisos
- Transferencias: Movimientos entre sucursales
- Activos: Bienes fijos
- Auditoría: Log de cambios

<img width="1449" height="652" alt="image" src="https://github.com/user-attachments/assets/6148b436-a1e2-4761-939b-8ca453d7b2da" />

### 6. Seguridad y Cumplimiento

#### 6.1 Seguridad
- Autenticación con Supabase Auth
- Autorización con RLS
- HTTPS en todas las comunicaciones
- Encriptación de datos sensibles
- Auditoría de accesos

#### 6.2 Cumplimiento
- Regulaciones Ministerio de Salud
- Normas de auditoría financiera
- Requisitos para IPO
- Protección de datos personales

### 7. Escalabilidad

#### 7.1 Horizontal
- Múltiples sucursales
- Múltiples usuarios concurrentes
- Múltiples regiones

#### 7.2 Vertical
- Más módulos
- Más integraciones
- Más reportes

### 8. Roadmap Tecnológico

| Fase | Duración | Entregables |
|------|----------|-------------|
| 1 | 3 meses | Auth, usuarios, sucursales, catálogo |
| 2 | 3 meses | Inventario, cajas, ventas |
| 3 | 3 meses | Transferencias, activos, auditoría |
| 4 | 3 meses | Call center, portal, entregas |
| 5 | 6 meses | Optimización, IPO readiness |


### 9. Diagrama Entidad-Relación

<img width="728" height="665" alt="image" src="https://github.com/user-attachments/assets/e035c1d4-9f11-41c7-a9ac-4a12409c30d4" />
