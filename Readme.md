## Testando o Flyway

- `Docker`
- `Pgsql`
- `Flyway`
- `Migration`

## Para confirmar que a tabela foi criada no Postgres
docker-compose exec db psql -U flyway -d flyway_teste -W -c "select * from flyway.flyway_schema_history"

## Checar a tabela pessoa
docker-compose exec db psql -U flyway -d flyway_teste -W -c "\d+ pessoa"

## Back up database
docker exec -u postgres proget-postgres pg_dump -Cc | xz > proget-backup-$(date -u +%Y-%m-%d).sql.xz

## Restore database from backup
xz -dc proget-backup-2021-03-02.sql.xz | docker exec -i -u postgres proget-postgres psql –set ON_ERROR_STOP=on –single-transaction

## Rodando o composer
`docker-compose up -d`


