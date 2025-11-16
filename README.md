# Power Apps Code App Scaffold

Este proyecto es una plantilla base para crear Power Apps Code Apps siguiendo las mejores prácticas de Microsoft y la preview actual.

## Prerrequisitos

- Visual Studio Code con la extensión Power Platform Tools
- Node.js (LTS v18.x o v20.x recomendado)
- Git
- Power Platform CLI (PAC CLI) actualizado
- Entorno Power Platform con Code Apps habilitado
- Licencias Power Apps Premium para usuarios finales
- Cuenta de Azure (si usas conectores Azure)

## Configuración inicial

1. Clona este repositorio y entra en la carpeta del proyecto.
2. Instala dependencias:

   ```sh
   npm install
   ```

3. Autentica y selecciona tu entorno Power Platform:

   ```sh
   pac auth create --environment {environment-id}
   pac env select --environment {environment-url}
   ```

4. Inicializa el proyecto Code App (si no está hecho):

   ```sh
   pac code init --displayName "Nombre de tu app"
   ```

5. Añade un conector (ejemplo Office 365 Users):

   ```sh
   pac connection list
   pac code add-data-source -a shared_office365users -c {connection-id}
   ```

6. Ejecuta en local:

   ```sh
   npm run dev
   ```

7. Despliega a Power Platform:

   ```sh
   npm run build
   pac code push
   ```

## Estructura del proyecto

```
src/
├── components/          # Componentes UI reutilizables
├── services/           # Servicios generados por PAC CLI
├── models/            # Modelos TypeScript generados
├── hooks/             # Custom hooks para Power Platform
├── utils/             # Utilidades
├── types/             # Tipos TypeScript
├── PowerProvider.tsx  # Inicialización Power Platform
└── main.tsx           # Entry point
```

## Ejemplo de integración conector Office 365 Users

```typescript
// import { Office365UsersService } from "@/services/Office365UsersService";
// const profile = await Office365UsersService.MyProfile_V2(
//   "id,displayName,jobTitle,userPrincipalName"
// );
// const photoData = await Office365UsersService.UserPhoto_V2(profile.data.id);
```

## Buenas prácticas

- Usa el puerto 3000 para desarrollo local
- `verbatimModuleSyntax: false` en tsconfig.json
- Configura vite.config.ts con `base: "./"` y alias de rutas
- No almacenes datos sensibles en el código
- Usa servicios/modelos generados por PAC CLI
- Implementa manejo de errores en operaciones de conectores
- Sigue las políticas de plataforma gestionada de Power Platform

## Limitaciones actuales

- CSP no soportado
- Sin integración Git Power Platform
- Sin soporte soluciones Dataverse
- Sin Application Insights nativo

## Recursos

- [Documentación oficial Power Apps Code Apps](https://learn.microsoft.com/power-apps/maker/code-apps/overview)
- [Repositorio de ejemplos Microsoft](https://github.com/microsoft/PowerAppsCodeApps)
