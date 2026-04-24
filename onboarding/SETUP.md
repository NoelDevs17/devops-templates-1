# Onboarding — Conectar MCP de Coolify en Antigravity

## Requisitos
- Antigravity instalado
- Acceso a LastPass/1Password de SmartTestingRD (para obtener el token)

## Pasos

### 1. Obtén tu API token
Pídele al equipo de infraestructura tu `developer-api-key`.
Este token tiene permisos de lectura y deploy únicamente.
**Nunca lo compartas ni lo pegues en el chat.**

### 2. Localiza el archivo de configuración de Antigravity

**Windows:**
```
C:\Users\<tu-usuario>\.gemini\antigravity\mcp_config.json
```

**Mac:**
```
~/.gemini/antigravity/mcp_config.json
```

Si el archivo no existe, créalo.

### 3. Agrega el MCP de Coolify

Abre el archivo y agrega o edita con este contenido:

```json
{
  "mcpServers": {
    "coolify-manager": {
      "type": "streamableHttp",
      "url": "https://coolify-mcp.smarttesting.com.do/mcp",
      "headers": {
        "Authorization": "Bearer <TU-TOKEN-AQUI>"
      }
    }
  }
}
```

Reemplaza `<TU-TOKEN-AQUI>` con tu token real.

### 4. Reinicia Antigravity
Cierra y vuelve a abrir Antigravity completamente.

### 5. Verifica que funciona
En Antigravity escribe:

> dame el status de los proyectos en coolify

Si ves una lista de proyectos, estás listo. ✓

## Primer deploy
Una vez conectado, para deployar un repo escribe en Antigravity:

> deploya <nombre-repo> en dev

El agente se encarga del resto.

## Problemas frecuentes

| Problema | Solución |
|---|---|
| No ve tools de Coolify | Verifica que reiniciaste Antigravity completamente |
| Error 401 | Tu token es incorrecto o expiró — pide uno nuevo al equipo |
| Error 403 | No tienes permisos para ese proyecto — contacta a infraestructura |
| No encuentra el repo | Verifica que el repo es público o que Coolify tiene acceso |
