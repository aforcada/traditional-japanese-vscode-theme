# Release Automation

Aquest document explica com automatitzar el procés de llançament d'una nova versió del tema VS Code.

## Configuració inicial

### 1. Configurar el token de VS Code Marketplace

Per poder publicar automàticament al marketplace de VS Code, necessites configurar un Personal Access Token (PAT):

1. Ves a https://dev.azure.com/
2. Crea un PAT amb els següents permisos:
   - **Marketplace**: `Acquire` i `Manage`
3. Afegeix aquest token com a secret al repositori de GitHub:
   - Ves a: `Settings` → `Secrets and variables` → `Actions` → `New repository secret`
   - Nom: `VSCE_TOKEN`
   - Valor: El teu Personal Access Token

### 2. Permisos del workflow

El workflow ja està configurat amb els permisos necessaris per:
- Crear commits
- Pujar tags
- Crear releases de GitHub

## Com fer un release

### Opció 1: Des de la interfície de GitHub (recomanat)

1. Ves a la pestanya **Actions** del repositori
2. Selecciona el workflow **Release**
3. Fes clic a **Run workflow**
4. Emplena els camps:
   - **Version**: El número de versió (exemple: `1.4.0`, `1.3.1`, `2.0.0`)
   - **Changelog**: El text del changelog per aquesta versió. Pots utilitzar `\n` per salts de línia.
     
     Exemple:
     ```
     - Nou tema: Traditional Japanese Sumi-e.\n- Millores de contrast a tots els temes.\n- Correcció d'errors a la sintaxi de Python.
     ```
5. Fes clic a **Run workflow**

### Opció 2: Des de la línia de comandos (avançat)

També pots executar el workflow utilitzant GitHub CLI:

```bash
gh workflow run release.yml \
  -f version="1.4.0" \
  -f changelog="- Nova funcionalitat 1.\n- Nova funcionalitat 2.\n- Correcció d'errors."
```

## Què fa el workflow automàticament?

El workflow executa els següents passos en ordre:

1. ✅ **Valida el format de la versió**: Assegura que sigui `X.Y.Z`
2. 📝 **Actualitza `package.json`**: Canvia el número de versió
3. 📋 **Actualitza `CHANGELOG.md`**: Afegeix una nova entrada amb la data actual
4. 💾 **Crea un commit**: Amb el missatge `chore: release version X.Y.Z`
5. 🏷️ **Crea un tag**: Amb el format `vX.Y.Z`
6. 📤 **Puja els canvis**: Tant el commit com el tag a GitHub
7. 📦 **Empaqueta l'extensió**: Crea el fitxer `.vsix`
8. 🚀 **Publica al Marketplace**: Publica automàticament al VS Code Marketplace
9. 🎉 **Crea GitHub Release**: Amb les notes del changelog i el fitxer `.vsix`

## Monitorització

- Pots veure el progrés del workflow a la pestanya **Actions**
- Cada execució proporciona un resum detallat al final
- Rebràs una notificació si hi ha errors

## Resolució de problemes

### Error: "Version must be in format X.Y.Z"
- Assegura't que la versió sigui en format semàntic: `1.4.0`, NO `v1.4.0` o `1.4`

### Error: "VSCE_TOKEN not found"
- Verifica que has configurat el secret `VSCE_TOKEN` correctament (veure Configuració inicial)

### Error al publicar al Marketplace
- Verifica que el token no hagi caducat
- Assegura't que el token tingui els permisos correctes (`Marketplace: Acquire, Manage`)

### Conflictes de versió
- Assegura't que la versió sigui superior a l'última publicada
- No reutilitzis números de versió anteriors

## Millores futures opcionals

Si vols afegir més funcionalitats al workflow, considera:

- Executar tests abans de publicar
- Validar que no hi hagi canvis sense cometre
- Notificacions per Slack/Discord/Email
- Changelog generat automàticament des dels commits
- Pre-releases o versions beta

---

**Nota**: Aquesta configuració està pensada per seguir les millors pràctiques de CI/CD mantenint la simplicitat i la facilitat d'ús.
