# VISIÓN DEL SISTEMA
## Sistema de Gestión Farmacéutica (SGF)

### 1. Introducción

#### 1.1 Propósito
Este documento define la visión, alcance y objetivos del Sistema de Gestión 
Farmacéutica (SGF), una plataforma integral diseñada para administrar la 
operación de una red de farmacias distribuidas en los principales centros 
comerciales y gasolineras de la República de Guatemala.

#### 1.2 Alcance
El SGF cubre los siguientes procesos de negocio:
- Control de inventario por sucursal, lote y fecha de vencimiento
- Gestión de ventas y pedidos
- Auditoría de flujo de efectivo en tiempo real
- Transferencias de medicamentos entre sucursales
- Control de activos fijos y patrimoniales
- Gestión de planilla y gastos operativos
- Coordinación de entregas al cliente final
- Integración futura con portal de clientes y call center

#### 1.3 Definiciones
| Término | Definición |
|---------|------------|
| SGF | Sistema de Gestión Farmacéutica |
| Sucursal | Punto de venta físico (farmacia o stand) |
| SKU | Código único de identificación de medicamento |
| Lote | Grupo de medicamentos con misma fecha de fabricación |
| RLS | Row Level Security (seguridad a nivel de fila) |
| RPC | Remote Procedure Call (llamada a procedimiento remoto) |

### 2. Posicionamiento

#### 2.1 Oportunidad de Negocio
La cadena de farmacias busca expandirse a nivel nacional aprovechando la 
infraestructura existente en centros comerciales y gasolineras. El SGF permitirá:
- Centralizar el control de todas las sucursales
- Auditar operaciones en tiempo real
- Optimizar la distribución de medicamentos
- Preparar la empresa para su entrada a la bolsa de valores

#### 2.2 Declaración del Problema
| Aspecto | Descripción |
|---------|-------------|
| **El problema de** | Falta de control centralizado sobre operaciones distribuidas |
| **afecta a** | Gerencia general, auditores, gerentes de sucursal, clientes finales |
| **cuyo impacto es** | Pérdidas por desabastecimiento, entregas tardías, falta de trazabilidad financiera |
| **una solución exitosa sería** | Plataforma web centralizada con control de inventario, auditoría en tiempo real y coordinación de entregas |

#### 2.3 Posición del Producto
El SGF se posiciona como una solución empresarial escalable, basada en 
tecnologías cloud modernas, que permite:
- Operación multi-sucursal desde una sola plataforma
- Trazabilidad completa de movimientos
- Auditoría financiera en tiempo real
- Integración con futuros canales de venta

### 3. Descripción de Stakeholders y Usuarios

#### 3.1 Resumen de Stakeholders
| Stakeholder | Representante | Rol |
|-------------|---------------|-----|
| Inversionistas | Junta Directiva | Financiamiento |
| Gerencia General | CEO | Decisiones estratégicas |
| Auditoría Interna | Auditor | Verificación de operaciones |
| Gerentes de Sucursal | Encargados | Operación local |
| Cajeros | Personal de venta | Transacciones |
| Clientes Finales | Público general | Consumo |

#### 3.2 Resumen de Usuarios
| Usuario | Descripción | Responsabilidades |
|---------|-------------|-------------------|
| Administrador | Gestión total del sistema | Usuarios, roles, configuración |
| Gerente Regional | Supervisión de sucursales | Reportes, auditoría |
| Gerente de Sucursal | Operación local | Inventario, cajas, personal |
| Cajero | Atención al cliente | Ventas, cobros |
| Bodeguero | Control de inventario | Recepción, transferencias |
| Operador Call Center | Atención telefónica | Pedidos, entregas |
| Auditor | Verificación | Consulta de movimientos |

#### 3.3 Entorno de Usuario
- **Interfaz web responsiva** accesible desde navegadores modernos
- **Acceso móvil** para gerentes y auditores
- **Terminales de punto de venta** para cajeros
- **Panel administrativo** para gestión central

#### 3.4 Necesidades Clave
| Necesidad | Prioridad | Solución |
|-----------|-----------|----------|
| Control de inventario por sucursal | Alta | Módulo de inventario con RLS |
| Auditoría de flujo de efectivo | Alta | Módulo de cajas y movimientos |
| Transferencias entre sucursales | Media | Módulo de transferencias |
| Control de activos fijos | Media | Módulo de activos |
| Gestión de planilla | Media | Módulo de gastos |
| Entregas a clientes | Media | Módulo de pedidos y entregas |
| Integración con call center | Baja | API REST para futura integración |

### 4. Características del Producto

#### 4.1 Características Principales
1. **Autenticación y Autorización**
   - Login con Supabase Auth
   - Roles: admin, gerente, cajero, auditor
   - Políticas RLS por sucursal

2. **Gestión de Sucursales**
   - CRUD de sucursales
   - Asignación de usuarios por sucursal
   - Estados: activa, inactiva, en mantenimiento

3. **Catálogo de Medicamentos**
   - SKU único
   - Categorías, laboratorios, presentaciones
   - Precios de compra y venta
   - Stock mínimo

4. **Inventario**
   - Por sucursal, lote y vencimiento
   - Movimientos trazables
   - Alertas de stock mínimo
   - Alertas de vencimiento

5. **Cajas**
   - Apertura con monto inicial
   - Movimientos de ingreso/egreso
   - Cierre con arqueo
   - Historial completo

6. **Ventas y Pedidos**
   - Validación de caja abierta
   - Validación de stock
   - Descuento transaccional
   - Registro automático en caja

7. **Transferencias** (futuro)
   - Solicitud, despacho, tránsito, recepción
   - Trazabilidad completa

8. **Auditoría** (futuro)
   - Log de cambios
   - Reportes de movimientos
   - Exportación de datos

#### 4.2 Supuestos y Dependencias
- Conectividad a internet estable en todas las sucursales
- Dispositivos con navegador moderno
- Capacitación del personal
- Integración futura con call center

### 5. Restricciones

#### 5.1 Restricciones de Diseño
- Arquitectura cloud (Vercel + Supabase)
- Frontend: Next.js 16 + React 19
- Backend: Server Actions + RPC
- Base de datos: PostgreSQL (Supabase)

#### 5.2 Restricciones de Implementación
- Presupuesto: US$5,000,000
- Plazo: 12 meses para fase 1
- Cumplimiento con regulaciones farmacéuticas
- Auditoría para entrada a bolsa de valores

#### 5.3 Restricciones de Negocio
- Operación 24/7 en algunas sucursales
- Múltiples monedas (futuro)
- Cumplimiento fiscal

### 6. Rangos de Calidad

| Atributo | Expectativa |
|----------|-------------|
| Disponibilidad | 99.9% uptime |
| Rendimiento | < 2s por transacción |
| Seguridad | RLS, HTTPS, encriptación |
| Escalabilidad | 500+ sucursales |
| Usabilidad | Capacitación < 4 horas |
| Mantenibilidad | Código modular, documentado |

### 7. Precedencia y Prioridad

| Prioridad | Característica | Fase |
|-----------|----------------|------|
| 1 | Autenticación y usuarios | Fase 1 |
| 2 | Sucursales y catálogo | Fase 1 |
| 3 | Inventario | Fase 1 |
| 4 | Cajas y ventas | Fase 1 |
| 5 | Transferencias | Fase 2 |
| 6 | Auditoría | Fase 2 |
| 7 | Activos y planilla | Fase 2 |
| 8 | Entregas y call center | Fase 3 |

### 8. Otros Requisitos del Producto

#### 8.1 Estándares Aplicables
- ISO 27001 (Seguridad de la información)
- Regulaciones del Ministerio de Salud de Guatemala
- Normas de auditoría financiera

#### 8.2 Requisitos de Sistema
- Node.js 20+
- Navegadores: Chrome, Firefox, Edge, Safari
- Conexión: 5 Mbps mínimo

#### 8.3 Requisitos de Documentación
- Manual de usuario
- Manual técnico
- Documentación de API
- Guía de despliegue
