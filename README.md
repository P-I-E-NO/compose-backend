# compose-backend
P.I.E.NO ready-to-pull infra

# start everything
be sure to pull every submodule:
```
git submodule update --init --recursive
```
1. run osrm stuff
    * `cd osrm`
    * `./stuff.sh`
2. run `docker compose up` and wait for everything to go online (once you see `api_gateway` logging stuff you're good to go)
3. run migrations inside `cloud-migrations` (for every folder inside it)
    * set the appropriate variables inside a `.env` file (copy the `.env.original`)
    * run `./migrate.sh`
4. run migrations for the ai part
    * `cd ml_pieno_predictions`
    * inside `migrations` run the `./migrate.sh` script
    * inside `last_seven` run the `./seed.sh` script
    * inside `table_predictions` run the `./table_preds.sh`
5. run `./predict.sh` in the root directory of this repo
6. run migrations for the distributors:
    * `cd ml_pieno_predictions/create_table_distributor`
    * run `./table_dist.sh`
    * `cd ml_pieno_predictions/push_distributors_db`
    * run `./insert_distributors.sh`
7. run migrations for the top distributors:
    * `cd ml_pieno_predictions/create_table_top_distributors`
    * run `./top_distributors.sh`

you should be all set! happy driving!