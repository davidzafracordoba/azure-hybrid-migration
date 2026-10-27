# Nomenclatura y etiquetas

Convención de nombres del proyecto **azure-hybrid-migration**, basada en las abreviaturas oficiales del Cloud Adoption Framework (CAF) de Microsoft.

## Dominios

| Uso | Nombre |
|---|---|
| Dominio de Active Directory local | `dzsystem.local` (NetBIOS: `DZSYSTEM`) |
| Dominio público (UPN, Entra ID, Azure DNS, App Service) | `dzsystem.es` |
| Zona DNS privada en Azure | `dzsystem.internal` |

## Patrón general

```
<tipo>-<empresa>-<función>-<región>[-<nº>]
```

- **Empresa:** `dzsystem`
- **Región principal:** West Europe → `weu`
- **Región secundaria** (réplicas, Site Recovery): North Europe → `neu`
- Todo en **minúsculas**, sin tildes ni espacios.

## Recursos

| Recurso | Abreviatura | Ejemplo |
|---|---|---|
| Management group | `mg` | `mg-dzsystem`, `mg-produccion`, `mg-pruebas` |
| Grupo de recursos | `rg` | `rg-dzsystem-red-weu`, `rg-dzsystem-vm-weu` |
| Red virtual | `vnet` | `vnet-hub-weu`, `vnet-servidores-weu`, `vnet-apps-weu` |
| Subred | `snet` | `snet-web`, `snet-gestion` |
| NSG | `nsg` | `nsg-snet-web` |
| ASG | `asg` | `asg-web`, `asg-gestion` |
| Tabla de rutas | `rt` | `rt-snet-aislada` |
| IP pública | `pip` | `pip-lb-web-weu` |
| Load Balancer | `lbe` / `lbi` | `lbe-web-weu` (externo), `lbi-web-weu` (interno) |
| Bastion | `bas` | `bas-hub-weu` |
| Máquina virtual (máx. 15 caracteres en Windows) | `vm` | `vm-intranet-01` |
| Scale Set | `vmss` | `vmss-web-weu` |
| Compute Gallery (solo letras, números, `_` y `.`) | `gal` | `gal_dzsystem_weu` |
| Cuenta de almacenamiento (3-24, solo minúsculas y números, única en Azure) | `st` | `stdzsystemfich01`, `stdzsystemhist01` |
| Container Registry (solo letras y números) | `cr` | `crdzsystem01` |
| Container Instance | `ci` | `ci-demo-weu` |
| Container App | `ca` | `ca-demo-weu` |
| Plan de App Service | `asp` | `asp-portal-weu` |
| App Service | `app` | `app-dzsystem-portal` |
| Log Analytics workspace | `log` | `log-dzsystem-weu` |
| Recovery Services vault | `rsv` | `rsv-dzsystem-weu` |
| Backup vault | `bvault` | `bvault-dzsystem-weu` |
| Action group | `ag` | `ag-dzsystem-admins` |

## Grupos de recursos

| Grupo | Contenido |
|---|---|
| `rg-dzsystem-red-weu` | VNets, NSG, ASG, rutas, Bastion, DNS |
| `rg-dzsystem-vm-weu` | VMs, VMSS, Load Balancer, galería de imágenes |
| `rg-dzsystem-storage-weu` | Cuentas de almacenamiento |
| `rg-dzsystem-apps-weu` | App Service, contenedores |
| `rg-dzsystem-monitor-weu` | Log Analytics, alertas, almacenes de copia |

## Etiquetas obligatorias

| Etiqueta | Valores | Ejemplo |
|---|---|---|
| `proyecto` | `az104-migracion` | `az104-migracion` |
| `entorno` | `prod`, `pruebas` | `prod` |
| `departamento` | `it`, `administracion`, `ventas` | `it` |
| `propietario` | nombre del responsable | `david` |

## Identidad local (referencia)

| Elemento | Convención | Ejemplo |
|---|---|---|
| OU raíz | Nombre de la empresa | `DZSYSTEM` |
| Grupos globales | `GG_<Departamento>` | `GG_IT` |
| Grupos locales de dominio (permisos) | `DL_<Recurso>_<R/RW>` | `DL_Ventas_RW` |
| UPN de usuario | `nombre.apellido@dzsystem.es` | `miguel.ruiz@dzsystem.es` |
