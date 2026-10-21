# TODO

## 07 MinIO
- [x] Infra, buckets, Boto3, presigned URL, IAM (`aluno123`)
- [ ] Seção 6 (nova): Mongo → `mongoexport` → `mc cp` para `datalake-bronze`
  - `mc` roda no container do Spark: usar `minio:9000` e `spark/data/` para os arquivos

## 08 Spark
- [x] Benchmark de formatos (`cargaSpark.ipynb`)
- [ ] (opcional) gráficos do README

## 09 Delta Lake
- [x] Bronze → Silver, escrita/leitura Delta, MERGE e histórico (`delta.ipynb`)
- [ ] 4.3 Gold: ranking de pilotos e de construtores (`GROUP BY` + `SUM(points)`)

## Arrumação
- [ ] Apagar `spark/mc` (binário não usado; o da imagem é outro)

## Sincronizar com o professor
`git fetch upstream` → `git log --oneline HEAD..upstream/main` → `git merge upstream/main` → `git push`
