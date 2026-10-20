# Espelho da imagem Silo

Este repositorio preserva uma copia verificavel da imagem de object storage usada pela iaSolution. Ele nao e um fork do codigo-fonte e nao altera o Silo: o workflow copia o artefato OCI original, incluindo todas as arquiteturas, para o GitHub Container Registry.

## Imagem preservada

- Origem: `docker.io/pgsty/silo@sha256:635197cb9f36d01bee221d34d1c7d7960f6a95c48b0b6c01d99cd13bdae51a46`
- Release: `RELEASE.2026-09-16T00-00-00Z`
- Espelho: `ghcr.io/leonardosfreire/silo:RELEASE.2026-09-16T00-00-00Z`
- Manifesto esperado: `sha256:635197cb9f36d01bee221d34d1c7d7960f6a95c48b0b6c01d99cd13bdae51a46`

O workflow manual `.github/workflows/mirror-silo.yml` verifica o digest da origem, executa `skopeo copy --all --preserve-digests` e compara novamente o manifesto publicado no GHCR.

## Recuperacao

Em uma contingencia, confirme primeiro o digest publicado:

```bash
docker buildx imagetools inspect ghcr.io/leonardosfreire/silo:RELEASE.2026-09-16T00-00-00Z
```

Depois use a referencia imutavel exibida pelo GHCR. Alterar uma instalacao em producao deve ser uma operacao separada, com verificacao de volume, variaveis `MINIO_*`, portas `9000/9001` e health check `/minio/health/ready`.

## Origem, autoria e licenca

Silo e um fork comunitario do MinIO mantido pela PGSTY. Este repositorio e apenas um espelho operacional da iaSolution e nao representa autoria, afiliacao ou suporte ao projeto.

A imagem e o codigo do Silo permanecem sob `AGPL-3.0-or-later`, com os avisos e atribuicoes dos projetos originais. Consulte:

- https://github.com/pgsty/silo
- https://github.com/pgsty/silo/releases/tag/RELEASE.2026-09-16T00-00-00Z
- https://github.com/pgsty/silo/blob/main/COMPLIANCE.md
- https://silo.pgsty.com/compatibility/migration/

