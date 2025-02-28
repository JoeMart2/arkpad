# arkpad-main

# Git Submodules with Docker Setup

## Prerequisites

Ensure you have the following installed on your system:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Cloning the Repository with Submodules

If you are cloning the repository for the first time, use:

```sh
git clone --recurse-submodules <repo_url>
cd <repo_name>
```

If you have already cloned the repository but need to fetch submodules, run:

```sh
git submodule update --init --recursive
```

## Updating Submodules

To fetch the latest changes from submodules, use:

```sh
git submodule update --remote --merge
```

If you want to pull changes and reset to the latest commit from the submodule’s remote branch, use:

```sh
git submodule foreach git pull origin main
```

_(Change `main` to the relevant branch if needed.)_

## Docker Setup

### Building and Running the Containers

Ensure you are inside the project directory, then run:

```sh
docker-compose up --build -d
```

This will build and start the Docker containers in detached mode.

### Stopping the Containers

To stop running containers, use:

```sh
docker-compose down
```

### Checking Running Containers

```sh
docker ps
```

## Working with Submodules Inside Docker

If you need to access a submodule inside a container, you can use:

```sh
docker exec -it <container_name> bash
```

Then navigate to the submodule directory and perform necessary actions.

## Troubleshooting

- **Submodule folder is empty**  
  Ensure you ran:

  ```sh
  git submodule update --init --recursive
  ```

  after cloning.

- **Docker build fails due to missing submodules**  
  Verify that the submodules exist inside the `docker build` context by running:

  ```sh
  ls <submodule_path>
  ```

## Removing a Submodule

If you no longer need a submodule, remove it with:

```sh
git submodule deinit -f <submodule_path>
git rm -rf <submodule_path>
rm -rf .git/modules/<submodule_path>
```
