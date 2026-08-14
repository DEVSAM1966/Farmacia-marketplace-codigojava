# Issue FAR-001: Automatización generación de Issues técnicas

**Estado**: Open  
**Componente**: Arquitectura hexagonal / Automation  
**Etiquetas**: technical, architecture, triaged  
**Creado**: 2026-08-14  
**Relacionado**: `.github/DOCUMENTATIONS/issue-automation.md`, `.github/ISSUE_TEMPLATE/tecnica.yml`

## Descripción
Issue fundador para documentar y automatizar el proceso de generación de Issues técnicas en el repositorio Farmacia-marketplace-codigojava.

## Contexto
Como parte del proyecto backend de marketplace parafarmacéutico, se requiere estandarizar la creación de Issues técnicas siguiendo la arquitectura hexagonal y las restricciones de venta por internet de productos de parafarmacia.

## Qué se automatiza
- Creación de Issues con template `.github/ISSUE_TEMPLATE/tecnica.yml`
- Etiquetado automático: `technical`, `architecture`, `triaged`
- Numeración consecutiva: `[FAR-001]`, `[FAR-002]`, etc.
- Validación de restricción parafarmacéutica: productos no medicamentosos por internet

## Plantilla utilizada
- Archivo: `.github/ISSUE_TEMPLATE/tecnica.yml`
- Campos: componente, decisión técnica, estimación, validación de producto

## Documentación generada
- `.github/DOCUMENTATIONS/issue-automation.md` - Documentación completa del proceso
- Directorio `.github/ISSUE_HISTORY/` para copias de issues creados

## Checklist de validación
- [ ] Issue creado con título `[FAR-001]`
- [ ] Template aplicado correctamente
- [ ] Labels asignados: `technical`, `architecture`, `triaged`
- [ ] Referencia a AGENTS.md y restricciones parafarmacéuticas
- [ ] Documentación `.github/DOCUMENTATIONS/issue-automation.md` actualizada
- [ ] Directorio `.github/ISSUE_HISTORY/` preparado para copias

## Comandos de lanzamiento

**Opción 1 - GitHub CLI**:
```bash
gh issue create --title "[FAR-001] Automatización generación de Issues técnicas" \
  --template .github/ISSUE_TEMPLATE/tecnica.yml \
  --label "technical" --label "architecture" --label "triaged"
```

**Opción 2 - API curl**:
```bash
curl -X POST \
  -H "Authorization: token $GITHUB_TOKEN" \
  -H "Accept: application/vnd.github+json" \
  https://api.github.com/repos/DEVSAM1966/Farmacia-marketplace-codigojava/issues \
  -d '{"title":"[FAR-001] Automatización generación de Issues técnicas","body":"...","labels":["technical","architecture","triaged"]}'
```

## Acciones posteriores (después de crear issue)

1. **Copiar contenido** del issue creado a `.github/ISSUE_HISTORY/FAR-001.md`
2. **Verificar** que el template se muestra correctamente en la UI de GitHub
3. **Probar** creación de segunda issue `[FAR-002]` para confirmar numeración consecutiva
4. **Revisar** flujo completo y ajustar documentación si es necesario

## Relación con el proyecto

Este Issue respalda directamente las directrices del `AGENTS.md`:
- ✅ Arquitectura hexagonal (componentes: domain/application/adapters/config)
- ✅ Validación de medicamentos (checkbox producto permitido según normativa)
- ✅ Perfiles dev/test/prod (mencionados en descripción y convenios)
- ✅ Calidad de código y validación en CI
- ✅ Convenciones de numeración [FAR-XXX]
- ✅ Flujo Feature branch → PR → main