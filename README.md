# switch-localenv
if you want to change your local env file to test multiple environment, you can use it. it also helps to share the .env variable to be used in the shell.

## Features

- easily switch between multiple local environment variables creating .env.local file
- share env variables between .env files with shell variables automatically
- safe for existing .env.local file (auto backup under `~/.env-temp` folder)


## Requirement

- install dotenv module since this library take advantage of dotenv
- add env_files folder under .gitignore to prevent sharing your secret value to be merged.

## How to Install

### Make folder/file structure
just download this under env_files folder
you will have file structures like this:

```text
L env_files
  L local-env-tool
    L options
      L dev (the env name that you will use)
      L qa (the env name that you will use)
    L export-local.sh
    L localEnvLoader.js
    L use-local.sh
    L template
```

In above structure, dev, qa, and template are the env file that you have.
template file is what will be copied in case the environment that you selected does not exist yet.
If you don't know yet, just make a new file like below.

```bash
TEST=yes
```

Not only template file, but also all the files under options should include TEST=XXX.
the value does not need to be `yes`. But it should not be empty. This variable will be used to check if the variables are exported to be usable environment variables.

### add alias for the convenience

add below alias in `.zshrc`(or your shell init file) for the convenience.

```bash
alias local="source ./env_files/local-env-tool/use-local.sh"
```

## How to use it

you can simply run it like this:

```
local dev
```

