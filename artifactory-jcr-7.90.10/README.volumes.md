### Artifactory Single Node Docker Compose Installation using Docker Volumes
1. Create Docker volumes.
```
docker volume create --name=artifactory_data
docker volume create --name=postgres_data
```
2. Add the entries in the `.env` file.

Avoid adding duplicate entries in the `.env` file.
```
echo -e "JF_SHARED_NODE_IP=$(hostname -i)" >> .env
echo -e "JF_SHARED_NODE_ID=$(hostname -s)" >> .env
echo -e "JF_SHARED_NODE_NAME=$(hostname -s)" >> .env
```
NOTE: Use `curl ifconfig.me` for `hostname -i` on MacOS
```
echo -e "JF_SHARED_NODE_IP=$(curl ifconfig.me)" >> .env
```
3. Manage Artifactory using native Docker Compose commands: `docker-compose -p rt <action> command`.
Run these commands from the extracted folder.
```
docker-compose -p rt up -d
docker-compose -p rt ps
docker-compose -p rt down
```
