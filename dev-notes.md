# C4 Model

https://www.youtube.com/watch?v=x2-rSnhpw0g

# Docker

https://github.com/abiosoft/colima/blob/main/docs/FAQ.md#docker-socket-location

export DOCKER_HOST="unix://${HOME}/.colima/default/docker.sock"

# Building spring boot image with docker

https://www.codejava.net/docker/create-docker-image-for-spring-boot-app

https://medium.com/swlh/build-a-docker-image-using-maven-and-spring-boot-58147045a400

# K8s

## Installation de minikube

https://infoheap.com/mac-m1-install-kubernetes-wiht-minikube/


75774P@PMP00555 cloud-native-spring-in-action % minikube start
zsh: command not found: minikube
75774P@PMP00555 cloud-native-spring-in-action % brew install minikube
Running `brew update --auto-update`...
==> Auto-updated Homebrew!
Updated 3 taps (homebrew/cask-versions, homebrew/core and homebrew/cask).
==> New Formulae
aarch64-elf-gdb               conan@1                       gfold                         ksops                         mdt                           pgvector                      sql-migrate                   wazero
adr-viewer                    conduit                       go-feature-flag-relay-proxy   lacework-cli                  musikcube                     phoneinfoga                   streamvbyte                   wpebackend-fdo
aichat                        define                        golines                       libansilove                   notify                        picotool                      teip                          xurls
aicommits                     dexter                        hexer                         libdvbcsa                     okta-aws-cli                  portal                        tkey-ssh-agent                zlint
arttime                       dutree                        hq                            libgit2@1.5                   ol                            renovate                      trippy                        zpaqfranz
base16384                     enchive                       hz                            libpaper                      opal                          service-weaver                tt
benerator                     flavours                      imessage-exporter             libwpe                        openssl@3.0                   sing-box                      typst
blocky                        garble                        keyring                       llvm@15                       pfetch-rs                     smartdns                      victoriametrics
==> New Casks
alex313031-thorium                       doppler                                  godot3                                   libreoffice-still-language-pack          orbstack                                 usmart-trade
bazecor                                  edrawmind                                hummingbird                              minisim                                  prism                                    vbrokers
cursor                                   fightcade                                imazing-converter                        moneymanager                             rsyncui                                  zed
dehelper                                 firefox-cn                               irpf2023                                 mullvad-browser                          typora-dev

You have 7 outdated formulae and 1 outdated cask installed.

Error: Cannot install under Rosetta 2 in ARM default prefix (/opt/homebrew)!
To rerun under ARM use:
arch -arm64 brew install ...
To install under x86_64, install Homebrew into /usr/local.
75774P@PMP00555 cloud-native-spring-in-action % arch -arm64 brew install minikube
==> Downloading https://formulae.brew.sh/api/formula.jws.json
######################################################################## 100.0%
==> Downloading https://formulae.brew.sh/api/cask.jws.json
######################################################################## 100.0%
==> Fetching dependencies for minikube: kubernetes-cli
==> Fetching kubernetes-cli
==> Downloading https://ghcr.io/v2/homebrew/core/kubernetes-cli/manifests/1.26.3
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/kubernetes-cli/blobs/sha256:79c51d0bc3eb3375e74813ef558efa97362216f4e0ec74d1a3dce2524ec119a4
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:79c51d0bc3eb3375e74813ef558efa97362216f4e0ec74d1a3dce2524ec119a4?se=2023-04-04T13%3A05%3A00Z&sig=OXUsXuAPUlURKu3j6VywzSdneudZw06o6b6ieVMmzUg%3D&sp=r&spr=https&s
######################################################################## 100.0%
==> Fetching minikube
==> Downloading https://ghcr.io/v2/homebrew/core/minikube/manifests/1.30.0
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/minikube/blobs/sha256:4abb42b1f517abb77df0b65882a5ccbca4551881c546da812c94916d7460bf42
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:4abb42b1f517abb77df0b65882a5ccbca4551881c546da812c94916d7460bf42?se=2023-04-04T13%3A05%3A00Z&sig=fcx2Pa%2FgNpjdeYAkYNDhWLSDBdww4EjRLkRR9kxqSLo%3D&sp=r&spr=https
######################################################################## 100.0%
==> Installing dependencies for minikube: kubernetes-cli
==> Installing minikube dependency: kubernetes-cli
==> Pouring kubernetes-cli--1.26.3.arm64_monterey.bottle.tar.gz
🍺  /opt/homebrew/Cellar/kubernetes-cli/1.26.3: 231 files, 56.4MB
==> Installing minikube
==> Pouring minikube--1.30.0.arm64_monterey.bottle.tar.gz
==> Caveats
zsh completions have been installed to:
/opt/homebrew/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/minikube/1.30.0: 9 files, 77.5MB
==> Running `brew cleanup minikube`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> Caveats
==> minikube
zsh completions have been installed to:
/opt/homebrew/share/zsh/site-functions
75774P@PMP00555 cloud-native-spring-in-action % 


## Démarrage de minikube

75774P@PMP00555 cloud-native-spring-in-action % minikube start
😄  minikube v1.30.0 sur Darwin 12.6 (arm64)
✨  Choix automatique du pilote docker. Autres choix: qemu2, ssh
📌  Utilisation du pilote Docker Desktop avec le privilège root
👍  Démarrage du noeud de plan de contrôle minikube dans le cluster minikube
🚜  Extraction de l'image de base...
💾  Téléchargement du préchargement de Kubernetes v1.26.3...
> preloaded-images-k8s-v18-v1...:  330.52 MiB / 330.52 MiB  100.00% 3.34 Mi
> gcr.io/k8s-minikube/kicbase...:  336.39 MiB / 336.39 MiB  100.00% 2.09 Mi
🔥  Création de docker container (CPUs=2, Memory=3872Mo) ...
❗  L'image n'a pas été construite pour la version actuelle de minikube. Pour résoudre ce problème, vous pouvez supprimer et recréer votre cluster minikube en utilisant les dernières images. Version de minikube attendue : v1.29.0 -> Version de minikube actuelle : v1.30.0
🐳  Préparation de Kubernetes v1.26.3 sur Docker 23.0.2...
▪ Génération des certificats et des clés
▪ Démarrage du plan de contrôle ...
▪ Configuration des règles RBAC ...
🔗  Configuration de bridge CNI (Container Networking Interface)...
▪ Utilisation de l'image gcr.io/k8s-minikube/storage-provisioner:v5
E0404 15:01:51.132836   86050 start.go:219] Unable to scale down deployment "coredns" in namespace "kube-system" to 1 replica: non-retryable failure while getting "coredns" deployment scale: Get "https://127.0.0.1:49154/apis/apps/v1/namespaces/kube-system/deployments/coredns/scale": read tcp 127.0.0.1:55292->127.0.0.1:49154: read: connection reset by peer - error from a previous attempt: read tcp 127.0.0.1:55290->127.0.0.1:49154: read: connection reset by peer
🔎  Vérification des composants Kubernetes...
❗  L'activation de 'default-storageclass' a renvoyé une erreur : running callbacks: [Error making standard the default storage class: Error listing StorageClasses: Get "https://127.0.0.1:49154/apis/storage.k8s.io/v1/storageclasses": read tcp 127.0.0.1:55293->127.0.0.1:49154: read: connection reset by peer - error from a previous attempt: read tcp 127.0.0.1:55291->127.0.0.1:49154: read: connection reset by peer]
🌟  Modules activés: storage-provisioner

### Troubleshooting

75774P@PMP00555 cloud-native-spring-in-action % minikube start --kubernetes-version=v1.27.0-rc.0
😄  minikube v1.30.0 sur Darwin 12.6 (arm64)

🙈  Fermeture en raison de K8S_DOWNGRADE_UNSUPPORTED : Impossible de rétrograder en toute sécurité le cluster Kubernetes v1.30.0 existant vers v1.27.0-rc.0
💡  Suggestion:

    1) Recréez le cluster avec Kubernetes 1.27.0-rc.0, en exécutant:
    
    minikube delete
    minikube start --kubernetes-version=v1.27.0-rc.0
    
    2) Créez un deuxième cluster avec Kubernetes 1.27.0-rc.0, en exécutant:
    
    minikube start -p minikube2 --kubernetes-version=v1.27.0-rc.0
    
    3) Utiliser le cluster existant à la version Kubernetes 1.30.0, en exécutant:
    
    minikube start --kubernetes-version=v1.30.0


75774P@PMP00555 cloud-native-spring-in-action % minikube delete
🔥  Suppression de "minikube" dans docker...
🔥  Suppression du conteneur "minikube" ...
🔥  Suppression du répertoire /Users/75774P/.minikube/machines/minikube…
💀  Le cluster "minikube" a été supprimé.
75774P@PMP00555 cloud-native-spring-in-action % minikube start --kubernetes-version=v1.27.0-rc.0
😄  minikube v1.30.0 sur Darwin 12.6 (arm64)
✨  Choix automatique du pilote docker. Autres choix: qemu2, ssh
📌  Utilisation du pilote Docker Desktop avec le privilège root
👍  Démarrage du noeud de plan de contrôle minikube dans le cluster minikube
🚜  Extraction de l'image de base...
💾  Téléchargement du préchargement de Kubernetes v1.27.0-rc.0...
> preloaded-images-k8s-v18-v1...:  327.71 MiB / 327.71 MiB  100.00% 4.78 Mi
🔥  Création de docker container (CPUs=2, Memory=3872Mo) ...
❗  L'image n'a pas été construite pour la version actuelle de minikube. Pour résoudre ce problème, vous pouvez supprimer et recréer votre cluster minikube en utilisant les dernières images. Version de minikube attendue : v1.29.0 -> Version de minikube actuelle : v1.30.0
🐳  Préparation de Kubernetes v1.27.0-rc.0 sur Docker 23.0.2...
▪ Génération des certificats et des clés
▪ Démarrage du plan de contrôle ...
▪ Configuration des règles RBAC ...
🔗  Configuration de bridge CNI (Container Networking Interface)...
▪ Utilisation de l'image gcr.io/k8s-minikube/storage-provisioner:v5
🔎  Vérification des composants Kubernetes...
🌟  Modules activés: storage-provisioner, default-storageclass
🏄  Terminé ! kubectl est maintenant configuré pour utiliser "minikube" cluster et espace de noms "default" par défaut.
75774P@PMP00555 cloud-native-spring-in-action % 




https://containers.goffinet.org/content/k8s-01-introduction-a-kubernetes/

## Kubectl

https://www.tutorialworks.com/kubernetes-imagepullbackoff/?utm_content=cmp-true
https://stackoverflow.com/questions/42564058/how-to-use-local-docker-images-with-minikube

# Start minikube
$ minikube delete
$ minikube start --kubernetes-version=v1.27.0-rc.0

# Set docker env
$ eval $(minikube docker-env)             # Pour que minikube utilise le démon docker

# Run in minikube
$ kubectl run catalog-service --image=catalog-service:0.0.1-SNAPSHOT --image-pull-policy=Never

## You can verify the creation of the Deployment object as follows:
$ kubectl get deployment
NAME              READY   UP-TO-DATE   AVAILABLE   AGE
catalog-service   1/1     1            1           7s
Behind the scenes, Kubernetes created a Pod for the application defined in the Deployment resource.
You can verify the creation of the Pod object as follows:

$ kubectl get pods
NAME              READY   STATUS    RESTARTS   AGE
catalog-service   1/1     Running   0          10s

# Create service
$ kubectl create deployment catalog-service --image=catalog-service:0.0.1-SNAPSHOT

# Expose service
$ kubectl expose deployment catalog-service --name=catalog-service --port=8080

# Forward port
$ kubectl port-forward service/catalog-service 8000:8080

# Clean up

$ kubectl delete deployment catalog-service
$ kubectl delete service catalog-service