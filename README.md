Deploy Docker Compose
=========

Le rôle Ansible deploy-docker-compose est conçu pour faciliter le déploiement d'applications conteneurisées en utilisant Docker et Docker Compose sur un serveur distant.

Il automatise les tâches suivantes :

Copie du fichier docker-compose.yml et du fichier optionnel .env depuis votre machine locale vers le serveur distant.
Création du répertoire de destination sur le serveur distant si nécessaire.
Si des Dockerfiles sont fournis, le rôle construit les images Docker correspondantes sur le serveur distant.
Enfin, le rôle lance les conteneurs en utilisant la commande docker-compose up.
Ce rôle est très flexible, il permet une configuration personnalisée via des variables, comme le chemin du fichier docker-compose.yml, le répertoire de destination sur le serveur distant, le chemin des Dockerfiles et les noms des images Docker à construire.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

docker_compose_file: Le chemin vers votre fichier docker-compose.yml sur votre machine locale.
docker_compose_dest: Le répertoire de destination sur le serveur distant où le fichier docker-compose.yml sera copié.
var_env_file: (Optionnel) Le chemin vers le fichier .env sur votre machine locale, qui sera copié dans le répertoire docker_compose_dest sur le serveur distant.
docker_files: (Optionnel) Une liste des chemins vers les Dockerfiles sur votre machine locale qui seront utilisés pour construire des images Docker.
docker_images: (Optionnel) Une liste des noms d'images Docker à construire. Chaque nom d'image doit correspondre à un Dockerfile dans la liste docker_files.

Dependencies
------------

- docker 
- docker-compose

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
