# TODO

## AV1 — entrega até qua 04/11 12:00 (Moodle, um .zip)
Notebooks em `spark/notebooks/` (kernel do container do Spark, porta 8889). Saídas preservadas!

Subir antes: `mongodb/` e `spark/` (`docker compose up -d`). MinIO já está rodando.

- [ ] **Q1 (1,0) Ambiente** — `Q1_ambiente.ipynb`
  - [ ] Token mascarado: `!jupyter server list | sed -E 's/token=[a-f0-9]+/token=****/'`
  - [ ] Não há senha (`spark/config/` não tem `jupyter_server_config.json`) → caminho do item a)
- [ ] **Q2 (2,0) AED Censo no Mongo** — `Q2_aed_censo.ipynb`
  - [ ] Conectar em `mongo_service:27017` (dados já em `inep.ies`)
  - [ ] Instituições por região (`aggregate`), docentes por gênero (`QT_DOC_EX_FEMI`/`MASC`), instituições por UF (`NO_UF_IES`)
  - [ ] Um gráfico por consulta, com título e eixos
- [ ] **Q3 (3,5) Benchmark** — copiar `cargaSpark.ipynb` → `Q3_benchmark.ipynb`
  - [ ] Bucket **`datalake`** (não `datalake-bronze`): mudar `BUCKET`, `base` e o `mc du`
  - [ ] Tabela (pandas) + gráficos com os números **medidos**, não os do README
  - [ ] d) Discussão OLAP vs streaming em célula markdown, com suas palavras
- [ ] **Q4 (3,5) Ingestão** — `Q4_ingestao.ipynb`
  - [ ] Terminal: `curl` do `sampledata.archive` → `mongorestore` → `mongoexport` (3 × `.jsonl`) — colar comandos/saídas no notebook
  - [ ] Copiar `mongodb/datasets/raw` → `spark/data/raw` (o container do Spark só enxerga `spark/data`)
  - [ ] Notebook: contagens (pymongo), tamanhos e linhas (`!ls -lh`, `!wc -l`), `!mc mb local/datalake-bronze`, `!mc cp` em `mongodb/<banco>/<colecao>.jsonl`, `!mc ls -r`
  - Roteiro: seção 6 do `minio/README.md` do professor (no GitHub; ainda não foi feito o merge)
- [x] **Credenciais**: `.env` em mongodb/minio/spark + `os.getenv` nos notebooks Q3/Q4 (Q2 deve nascer assim)
- [ ] **Re-executar Q3 inteiro** (Restart + Run All) — código mudou para `os.getenv`
- [ ] **Zip**: 4 notebooks + `spark/Dockerfile`, `spark/docker-compose.yml`, `minio/docker-compose.yml`, `mongodb/docker-compose.yml`. Sem `config/`, dados ou tokens.

## Depois da prova
- [ ] `git merge upstream/main` e remover o bloco Delta duplicado do `spark/Dockerfile`
- [ ] 09 Delta: 4.3 Gold (rankings)
- [ ] 07 MinIO: seção 6 (já coberta pela Q4)
- [ ] 10 Metabase (por último): porta 3000 conflita com o cassandra-web; fonte = Dremio?
- [ ] (opcional) gráficos do Spark

## Sincronizar com o professor
`git fetch upstream` → `git log --oneline HEAD..upstream/main` → `git merge upstream/main` → `git push`
