# compose-backend
P.I.E.NO ready-to-pull infra

# start everything
be sure to pull every submodule:
```
git submodule update --init --recursive
```
1. run `docker compose up` and wait for everything to go online (once you see `api_gateway` logging stuff you're good to go)
2. run migrations inside `cloud-migrations` (for every folder inside it)
    * set the appropriate variables inside a `.env` file (copy the `.env.original`)
    * run `./migrate.sh`
3. run migrations for the ai part
    * `cd ml_pieno_predictions`
    * inside `migrations` run the `./migrate.sh` script
    * inside `last_seven` run the `./seed.sh` script
    * inside `table_predictions` run the `./table_preds.sh`
4. run `./predict.sh` in the root directory of this repo
5. run migrations for the distributors:
    * `cd ml_pieno_predictions/table_distributors`
    * run `./table_dist.sh`
6. run migrations for the top distributors:
    * `cd ml_pieno_predictions/create_table_top_distributors`
    * run `./top_distributors.sh`
7. build additional apis:
    * `cd ml_pieno_predictions/api_obtain_data`
    * `./api_obtain_data.sh`
8. run osrm stuff
    * `cd osrm`
    * `./stuff.sh`

you should be all set! happy driving!