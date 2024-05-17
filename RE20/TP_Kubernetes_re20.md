# TP Kubernetes
## Auteur 

Philippe PEREIRA 
Ingénieur Infrastructure
Direction du Numérique
Université de Technologie de Troyes

## 1. Présentation de Kubernetes
### a. Introduction 

Kubernetes, souvent abrégé K8s, est une plateforme open-source conçue pour automatiser le déploiement, la mise à l'échelle et la gestion d'applications conteneurisées. Fruit de l'expertise de Google en matière d'orchestration de conteneurs, Kubernetes offre une solution robuste et portable, permettant aux développeurs de déployer des applications de manière efficace, tout en assurant une haute disponibilité et une gestion dynamique des ressources. Avec son architecture flexible et ses fonctionnalités avancées, Kubernetes s'impose comme l'outil incontournable pour orchestrer des environnements cloud et on-premise, facilitant ainsi le déploiement et la gestion des applications dans un monde informatique en constante évolution.
### b. Les fonctionnalités 

Les fonctionnalités de Kubernetes offrent plusieurs avantages :

- **Orchestration avancée :** Kubernetes automatise le déploiement, la mise à l'échelle et la gestion des conteneurs, simplifiant ainsi la gestion des applications complexes.
- **Portabilité :** Les applications Kubernetes peuvent être déployées de manière cohérente sur divers environnements, que ce soit en local, dans le cloud ou sur des infrastructures hybrides, assurant une grande portabilité.
- **Évolutivité :** Kubernetes facilite le dimensionnement des applications en fonction des besoins, permettant une montée en charge rapide et une réduction lorsque la demande diminue, assurant une utilisation efficace des ressources.
- **Déploiement déclaratif :** Les configurations de déploiement sont déclaratives, ce qui signifie que vous spécifiez l'état souhaité du système et Kubernetes s'occupe de le maintenir en conformité, simplifiant ainsi le processus de gestion.
- **Gestion des microservices :** Kubernetes facilite la gestion d'architectures basées sur des microservices, permettant aux développeurs de déployer, mettre à jour et équilibrer la charge des services indépendamment les uns des autres.
- **Automatisation des mises à jour :** Les mises à jour d'application peuvent être effectuées sans temps d'arrêt, assurant une disponibilité continue grâce aux fonctionnalités de déploiement par roulement (rolling updates).
- **Gestion des ressources :** Kubernetes optimise l'utilisation des ressources en assignant dynamiquement les ressources matérielles en fonction des besoins, ce qui permet d'économiser les coûts d'infrastructure.
- **Service Discovery et Load Balancing :** Kubernetes offre des services intégrés de découverte de services et d'équilibrage de charge, simplifiant la gestion des connexions entre les différents composants de l'application.
- **Gestion des secrets :** Kubernetes propose des mécanismes sécurisés pour gérer et distribuer les informations sensibles, comme les mots de passe et les clés d'API, de manière sécurisée.
- **Écosystème riche :** Kubernetes bénéficie d'un vaste écosystème d'outils, de plug-ins et de solutions tierces qui étendent ses fonctionnalités de base pour répondre à des besoins spécifiques.
### c. Les objets Kubernetes

- **Pod** : Instance la plus petite et la plus simple dans l'écosystème Kubernetes, représentant un conteneur et ses ressources associées.
- **Service** : Abstraction permettant d'exposer des pods et d'assurer la communication réseau entre eux.
- **ReplicaSet** : Garantit un nombre spécifié de réplicas (copies) en cours d'exécution des pods, assurant la haute disponibilité des applications.
- **Deployment** : Permet de déclarer, mettre à jour et gérer les applications déployées dans un cluster.
- **Namespace** : Un moyen de diviser les ressources d'un cluster Kubernetes en espaces virtuels distincts.
- **ConfigMap** : Stocke des données de configuration en dehors des conteneurs et les rend accessibles aux applications.
- **Secret** : Stocke des informations sensibles, telles que des mots de passe ou des clés d'API, de manière sécurisée.
- **Service Account** : Identité utilisée par les pods pour interagir avec l'API Kubernetes et d'autres ressources.
- **StatefulSet** : Gère des applications étatiques avec des identifiants réseau persistants pour chaque instance.
- **PersistentVolume (PV)** : Stockage persistant pouvant être réclamé par les pods, indépendamment de leur cycle de vie.
- **PersistentVolumeClaim (PVC)** : Une demande de stockage persistant faite par les pods pour utiliser un PersistentVolume.
- **Ingress** : Gère les règles d'accès externe aux services dans le cluster, fournissant un moyen d'acheminer le trafic HTTP et HTTPS.
- **DaemonSet** : S'assure qu'un pod s'exécute sur chaque nœud du cluster, garantissant une présence constante.
- **Job** : Gère des tâches à durée limitée, s'exécutant jusqu'à leur achèvement avec un ou plusieurs pods.

### d. K3S : Kubernetes Simplifié

Dans le cadre du TP, vous installerez K3S.

K3s est une distribution légère de Kubernetes, optimisée pour les environnements avec des ressources limitées, offrant une solution simplifiée et efficace pour le déploiement et la gestion d'applications conteneurisées.

### e. Architecture K8S/K3S

**Le nœud master :**
Un nœud master dans Kubernetes est un composant essentiel du cluster responsable de la gestion et du contrôle global de l'environnement. Il héberge les services du plan de contrôle, tels que l'API server, le scheduler et le controller manager, qui coordonnent et supervisent les opérations du cluster. Le nœud master prend des décisions sur les déploiements, la mise à l'échelle des applications, la gestion des ressources.

#### Les composants du nœud master :
> - `API Server` : Le composant central qui expose l'API Kubernetes. Il reçoit les demandes, effectue la validation, et les transmet aux autres composants pour l'exécution.
> - `Controller Manager` : Gère les contrôleurs qui régulent l'état désiré du cluster, s'assurant que les pods et autres ressources restent conformes aux spécifications définies.
> - `Scheduler` : Sélectionne les nœuds appropriés pour le déploiement des pods en fonction de politiques définies, assurant une distribution équilibrée des charges de travail.
> - `etcd` : Un magasin de données clé-valeur distribué utilisé pour stocker la configuration du cluster, l'état actuel, et d'autres informations cruciales.

**Les nœuds workers :**
Un nœud worker dans Kubernetes est un élément du cluster chargé d'exécuter les charges de travail réelles, représentées par des conteneurs. Contrairement au nœud master, le nœud worker ne gère pas les composants de contrôle du cluster, mais plutôt les pods qui hébergent les applications. Il exécute le kubelet pour interagir avec le nœud master, le runtime de conteneur pour lancer les conteneurs, et d'autres composants nécessaires pour la communication réseau, formant ainsi l'infrastructure d'exécution où les applications sont déployées et exécutées.

#### Les composants des nœuds workers
> - `Kubelet` : L'agent exécuté sur chaque nœud worker, responsable de l'exécution des conteneurs dans les pods et de l'interaction avec le nœud master.
> - `Container Runtime` : Le logiciel responsable de l'exécution des conteneurs. Docker, containerd et cri-o sont des exemples de runtimes pris en charge par Kubernetes.
> - `Kube-Proxy` : Gère la communication réseau entre les pods, assurant la connectivité réseau et l'équilibrage de charge au sein du cluster.

*Schéma d'architecture K8S/K3S*

![[k3_01.svg]]
### f. Le management des objets Kubernetes

Dans l'écosystème de Kubernetes (K8S), deux approches distinctes de gestion des objets émergent : ==le management déclaratif== et ==le management impératif==. 

Le management déclaratif, considéré comme la philosophie fondamentale de Kubernetes, se concentre sur la spécification de l'état désiré du système à l'aide de fichiers de configuration YAML ou JSON. Les utilisateurs déclarent l'état souhaité, et Kubernetes se charge d'appliquer les modifications nécessaires pour maintenir la cohérence avec cet état déclaré. 

À l'inverse, le management impératif implique la fourniture d'instructions explicites sur la manière dont les changements doivent être appliqués. Les commandes impératives, telles que `kubectl run` ou `kubectl expose`, dictent directement les actions à entreprendre. Bien que le management déclaratif offre une approche plus souple et résilience, le management impératif peut être utilisé pour des actions ponctuelles et rapides. La coexistence de ces deux approches permet aux utilisateurs de choisir la méthode qui convient le mieux à leurs besoins spécifiques dans la gestion et le déploiement d'applications sur la plateforme Kubernetes.

## 2. Installation de K3S

Grâce à K3S, un nœud peut assumer simultanément les fonctions de master et de worker, éliminant ainsi la nécessité de configurer un cluster complet pour explorer Kubernetes avec cette solution.

**Script d'installation** 
K3s propose un script qui simplifie l'installation en tant que service sur les systèmes basés sur systemd.

Pour installer K3s, exécutez la commande suivante : 

```shell
curl -sfL https://get.k3s.io | sh -
```

Affichez l'état du service K3S :

```shell
systemctl status k3s
```

Affichez l'inventaire des nœuds du cluster, y compris leur état de santé et disponibilité :

```shell
kubectl get nodes
```

*Sortie de la commande :* 

```
NAME         STATUS   ROLES                  AGE     VERSION
kubernetes   Ready    control-plane,master   5m20s   v1.27.7+k3s2
```

Afficher des détails étendus : 

```shell
kubectl get nodes -o wide
```

*Sortie de la commande :* 

```
NAME         STATUS   ROLES                  AGE   VERSION        INTERNAL-IP   EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
kubernetes   Ready    control-plane,master   62m   v1.27.7+k3s2   10.23.13.1   <none>        Ubuntu 20.04.6 LTS   5.4.0-167-generic   containerd://1.7.7-k3s1.27
```

Obtenir des informations sur l'état et la configuration du cluster :

```
kubectl cluster-info
```

*Sortie de la commande :* 

```
Kubernetes control plane is running at https://127.0.0.1:6443
CoreDNS is running at https://127.0.0.1:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
Metrics-server is running at https://127.0.0.1:6443/api/v1/namespaces/kube-system/services/https:metrics-server:https/proxy
```

## 4. Gestion des Pods dans Kubernetes

### a. Création d'un Pod avec un conteneur unique en utilisant l'Image NGINX

Pour générer un Pod, il est nécessaire de rédiger un fichier descriptif au format YAML (un manifeste) et de l'appliquer en utilisant la commande déclarative `kubectl apply`.

 Création du fichier `pod-nginx.yml`:

```yml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-demo
  labels:
    type: web
spec:
  containers:
  - image: nginx:latest
    name: nginx
```

Description de certains champs :
> - `apiVersion` : Indique la version de l'API Kubernetes utilisée pour créer l'objet. Dans l'exemple fourni, `v1` est la version de l'API.
> - `kind` : Spécifie le type d'objet à créer. Dans cet exemple, il s'agit d'un Pod.
> - `metadata` : Fournit des métadonnées pour l'objet, telles que le nom et les libellés (labels) du Pod. Cela aide à identifier de manière unique l'objet dans le cluster.
> - `name` : Le nom attribué au Pod, dans cet exemple, `nginx-demo`.
> - `labels` : Des étiquettes (labels) qui peuvent être utilisées pour identifier et organiser les objets. Dans cet exemple, le Pod est marqué avec le label `type: web`.
> - `spec` : Contient les spécifications détaillées de l'objet. Dans le contexte d'un Pod, il spécifie les conteneurs qui seront exécutés, avec des détails tels que l'image utilisée (`nginx:latest`) et le nom du conteneur (`nginx`).

Appliquez la configuration décrite dans le fichier `pod-nginx.yml` avec la commande suivante :

```shell
kubectl apply -f pod-nginx.yml
```

*Sortie de la commande :* 

```
pod/nginx-demo created
```

Affichez la liste des Pods :

```shell
kubectl get pods
```

*Sortie de la commande :* 

```
NAME         READY   STATUS    RESTARTS   AGE
nginx-demo   1/1     Running   0          2m31s
```

Affichez plus de détails : 

```
kubectl get pods -o wide
```

*Sortie de la commande :* 

```
NAME         READY   STATUS    RESTARTS   AGE     IP          NODE         NOMINATED NODE   READINESS GATES
nginx-demo   1/1     Running   0          5m36s   10.42.0.9   kubernetes   <none>           <none>
```

Observez les informations suivantes :
> - Adresse IP du Pod : `10.42.0.9`
> - Nom du noeud qui exécute le Pod : `kubernetes`
> - Nom du Pod : `nginx-demo`
> - READY : Le nombre de Pods actifs par rapport au nombre total de conteneurs définis dans le Pod.
> - Age :  Durée écoulée depuis la création du Pod.

Testez l'accès à la page web hébergée par votre Pod NGINX :

```
curl -s --noproxy '*' http://{{Pod_IP}}
```

L'option `--noproxy '*'` de curl permet d'ignorer les paramètres de proxy définis dans le système de la VM que vous utilisez dans le cadre de ce TP.

*Sortie de la commande :* 

```shell
curl -s --noproxy '*' http://10.42.0.9
```

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

### b. Création d'un Pod Multiconteneur

Instanciation d'un Pod composé de deux conteneurs échangeant des données au sein d'un volume partagé.

 Création du fichier `mcpod-demo.yaml`:

```yml
apiVersion: v1
kind: Pod
metadata:
  name: mcpod-demo
spec:
  containers:
  - name: nginx
    image: nginx:latest
    volumeMounts:
    - name: data
      mountPath: /usr/share/nginx/html
  - name: debian
    image: debian:latest
    volumeMounts:
    - name: data
      mountPath: /html
    command: ["/bin/sh", "-c"]
    args:
      - while true; do
          date >> /html/index.html;
          sleep 120;
        done

  volumes:
  - name: data
    hostPath:
      path: /home/re20/data
      type: DirectoryOrCreate
```

Description du fichier `mcpod-demo.yaml`:

`metadata`: Ce champ indique le nom attribué au Pod, ici désigné par `mcpod-demo`. Ce nom unique est utilisé pour identifier et gérer le Pod au sein du cluster.


`spec` : Ce champ détaille les spécifications du Pod. Plus précisément :

1. Le conteneur `nginx` :

```yml
containers:
  - name: nginx
    image: nginx:latest
    volumeMounts:
    - name: data
      mountPath: /usr/share/nginx/html
```

> - `name` : Le nom du conteneur (`nginx`).
> - `image` :  L'image Docker utilisée pour le conteneur (`nginx:latest`).
> - `volumeMounts` : Définit le montage du volume nommé `data` dans le chemin `/usr/share/nginx/html`. Cela permet le partage de données entre le conteneur et le volume.

2. Le conteneur `debian` :

```yml
 - name: debian
    image: debian:latest
    volumeMounts:
    - name: data
      mountPath: /html
    command: ["/bin/sh", "-c"]
    args:
      - while true; do
          date >> /html/index.html;
          sleep 120;
        done
```

> - `name` : Le nom du conteneur, ici `debian`.
> - `image` : L'image utilisée pour le conteneur (`debian:latest`).
> - `volumeMounts` : Définit le montage du volume nommé `data` dans le chemin `/usr/share/nginx/html`. Cela permet le partage de données entre le conteneur et le volume.
> - `command et args` : Ces champs spécifient la commande et les arguments pour le conteneur `debian`. Dans cet exemple, un script shell est exécuté en boucle, ajoutant la date actuelle à intervalles réguliers dans un fichier `index.html` situé dans le volume monté. 

3. Le volume utilisé par les deux conteneurs du Pod `mcpod-demo` :
> - `name` : Le nom du volume, ici `data`.
> - `hostPath` : Spécifie le type de volume utilisé, dans ce cas, un volume de type `hostPath`, qui monte un répertoire du système hôte dans le Pod.
>     - `path` : Le chemin absolu du répertoire sur le système hôte, ici `/home/re20/data`.
>     - `type` : Le type du volume, défini comme `DirectoryOrCreate`. Cela indique que le répertoire spécifié doit être créé s'il n'existe pas déjà. 

Ce volume permet le partage de données entre les conteneurs et l'hôte du cluster Kubernetes. Le conteneur `nginx`devrait donc publier la page web générée par le conteneur `debian`.

![[k3_02.png | 400]]

Appliquez la configuration décrite dans le fichier `mcpod-demo.yaml` avec la commande suivante :

```shell
kubectl apply -f mcpod-demo.yml
```

Affichez la liste des Pods exécutés : 

```shell
kubectl get pods -o wide
```

*Sortie de la commande :* 

```
NAME         READY   STATUS    RESTARTS   AGE   IP           NODE         NOMINATED NODE   READINESS GATES
nginx-demo   1/1     Running   0          69m   10.42.0.9    kubernetes   <none>           <none>
mcpod-demo   2/2     Running   0          54s   10.42.0.10   kubernetes   <none>           <none>
```

Affichez les informations détaillées concernant le Pod `mcpod-demo` :

```shell
kubectl describe pods mcpod-demo
```

Voici un aperçu des informations attendues :

> - `Name` : Le nom du Pod, dans ce cas, `mcpod-demo`.
> - `Namespace` : L'espace de noms dans lequel le Pod réside.
> - `Status` : L'état actuel du Pod, avec des détails sur le démarrage, l'arrêt ou d'autres événements liés au cycle de vie.
> - `IP Addresses` : Les adresses IP attribuées au Pod.
> - `Containers` : Les conteneurs en cours d'exécution dans le Pod, avec des détails sur l'image, l'état, et les ressources utilisées.
> - `Volumes` : Les volumes montés dans le Pod, avec des informations sur le chemin, le type, et d'autres attributs.
> - `Events` : Une liste chronologique des événements liés au Pod, tels que les démarrages, arrêts, erreurs, etc.

Affichez les logs d'un conteneur du Pod `mcpod-demo` :

```shell
kubectl logs {{POD_name}} -c {{Container_name}}
```

*Exemple :* 

```shell
kubectl logs mcpod-demo -c debian
```

Exécutez une commande dans un conteneur : 

```shell
kubectl exec {{POD_name}} -c {{Container_name}} -- {{cmd}}
```

*Exemple :* 

```shell
kubectl exec mcpod-demo -c debian -- cat /html/index.html
```
```
Thu Dec  7 22:35:31 UTC 2023
Thu Dec  7 22:37:31 UTC 2023
Thu Dec  7 22:39:31 UTC 2023
Thu Dec  7 22:41:31 UTC 2023
Thu Dec  7 22:43:31 UTC 2023
Thu Dec  7 22:45:31 UTC 2023
Thu Dec  7 22:47:31 UTC 2023
Thu Dec  7 22:49:31 UTC 2023
Thu Dec  7 22:51:31 UTC 2023
```

Assurez-vous que le répertoire `data`à correctement été créé :

```shell
ls -lhar /home/re20/
```
```
drwxr-xr-x 2 root root 4.0K Dec  7 22:35 data
```

Affichez le contenu du fichier `/home/re20/index.html`.

```shell
tail -f /home/re20/data/index.html
```
```
Thu Dec  7 22:37:31 UTC 2023
Thu Dec  7 22:39:31 UTC 2023
Thu Dec  7 22:41:31 UTC 2023
Thu Dec  7 22:43:31 UTC 2023
Thu Dec  7 22:45:31 UTC 2023
Thu Dec  7 22:47:31 UTC 2023
Thu Dec  7 22:49:31 UTC 2023
Thu Dec  7 22:51:31 UTC 2023
Thu Dec  7 22:53:31 UTC 2023
Thu Dec  7 22:55:31 UTC 2023
```

Affichez la page web hébergée par votre Pod `mcpod-demo` :

```shell
curl -s --noproxy '*' http://{{mcpod-demo_ip}}
```

*Exemple :* 

```shell
curl -s --noproxy '*' http://10.42.0.10
```
```
Thu Dec  7 22:35:31 UTC 2023
Thu Dec  7 22:37:31 UTC 2023
Thu Dec  7 22:39:31 UTC 2023
Thu Dec  7 22:41:31 UTC 2023
Thu Dec  7 22:43:31 UTC 2023
Thu Dec  7 22:45:31 UTC 2023
Thu Dec  7 22:47:31 UTC 2023
Thu Dec  7 22:49:31 UTC 2023
Thu Dec  7 22:51:31 UTC 2023
Thu Dec  7 22:53:31 UTC 2023
Thu Dec  7 22:55:31 UTC 2023
```

### c. Test de la persistance des données

La persistance des données dans Kubernetes est assurée par l'utilisation de volumes, permettant aux conteneurs de stocker des informations de manière persistante et de partager des données entre les redémarrages et les mises à jour d'applications.

Supprimez puis, recréez le Pod `mcpod-demo` :

```shell
kubectl delete pod mcpod-demo
kubectl apply -f mcpod-demo.yml
```

Utilisez la commande `kubectl get pods -o wide` pour obtenir l'adresse IP du Pod nouvellement créé puis, utilisez la commande `curl`pour affiché la page hébergée par le Pod :


```shell
curl -s --noproxy '*' http://10.42.0.11
```
```
Thu Dec  7 22:35:31 UTC 2023
Thu Dec  7 22:37:31 UTC 2023
Thu Dec  7 22:39:31 UTC 2023
Thu Dec  7 22:41:31 UTC 2023
Thu Dec  7 22:43:31 UTC 2023
Thu Dec  7 22:45:31 UTC 2023
Thu Dec  7 22:47:31 UTC 2023
Thu Dec  7 22:49:31 UTC 2023
Thu Dec  7 22:51:31 UTC 2023
Thu Dec  7 22:53:31 UTC 2023
Thu Dec  7 22:55:31 UTC 2023
Thu Dec  7 22:57:31 UTC 2023
Thu Dec  7 22:59:31 UTC 2023
```

**Vous pouvez observer que les données n'ont pas été perdues.**

### d. Utilisation d'une commande impérative pour la création un Pod
  
La commande `kubectl run` permet de créer un Pod sans avoir à définir un fichier YAML au préalable. 

Exemple :

```shell
kubectl run nginx-pod2 --image=nginx --restart=Always
```

La création est impérative, ce qui signifie que vous spécifiez directement les paramètres nécessaires lors de la commande. Cela est rapide et pratique pour des tâches simples, mais cela peut être peu flexible pour des scénarios plus complexes nécessitant des paramètres personnalisés.

En résumé, la création impérative est rapide mais peut être limitée, tandis que la création déclarative offre une plus grande flexibilité et est recommandée pour des déploiements plus complexes et gérables sur le long terme.

==Supprimez les pods créés précédemment, car ils ne seront plus nécessaires pour la suite.==

## 5. Gestion de ReplicaSets dans Kubernetes

Un ReplicaSet dans Kubernetes est un contrôleur qui garantit qu'un nombre spécifié de répliques identiques d'un pod tournent en permanence dans le cluster. Il assure la haute disponibilité des applications en surveillant constamment l'état des pods et en en créant ou supprimant automatiquement pour maintenir le nombre souhaité. Cette fonctionnalité permet d'assurer la résilience des applications.

### a. Mise en œuvre d'un ReplicaSet  

Dans cette section, vous allez mettre en place un ReplicaSet pour déployer trois instances d'un Pod, chacun abritant un unique conteneur `nginx`.

Création du fichier `rs-demo.yaml` :

```yml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: rs-demo
  labels:
    app: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx
```

Description des champs présents dans le fichier : 

> - `apiVersion` : Version typique pour les objets de type ReplicaSet (`apps/v1`).
> - `kind` : Spécifie le type d'objet à créer (`ReplicaSet`).

> - `metadata` : Contient des métadonnées.
> 	- `name` : Le nom attribué au ReplicaSet (`rs-demo`).
> 	- `labels` : Label associé au ReplicaSet (`app: web`).

> - `spec` : Détaille les spécifications du ReplicaSet.
> - `replicas` : Indique le nombre de répliques que le ReplicaSet doit maintenir (3).
> - `selector` : Spécifie le sélecteur utilisé pour identifier les pods qu'il doit gérer.
>     - `matchLabels` : Les labels qui doivent correspondre pour qu'un pod soit géré par ce `ReplicaSet`, par exemple `app: web`.
> - `template` : Contient la description du pod que le ReplicaSet doit déployer.
>     - `metadata` : Les métadonnées du pod.
>         - `labels` : Les labels associés au pod (`app: web`).
>     - `spec` : Les spécifications du pod.
>         - `containers` : La liste des conteneurs dans le pod.
>             - `name` : Le nom du conteneur (`nginx`).
>             - `image` : L'image Docker utilisée pour le conteneur (`nginx`).

Utilisez la commande suivante pour créer le ReplicaSet `rs-demo`: 

```shell
Kubectl apply -f rs-demo.yaml
```

Affichez la liste des ReplicaSets du cluster : 

```shel
kubectl get rs
```
```
NAME      DESIRED   CURRENT   READY   AGE
rs-demo   3         3         3       21s
```

La commande sortie de la commande présente le ReplicaSet `rs-demo` avec trois répliques, toutes opérationnelles et prêtes, créées il y a 21 secondes.

Affichez la liste des Pods en cours d'exécution dans le cluster :

```shell
kubectl get pods -o wide
```
```
NAME            READY   STATUS    RESTARTS   AGE     IP           NODE         NOMINATED NODE   READINESS GATES
rs-demo-lthhg   1/1     Running   0          4m43s   10.42.0.15   kubernetes   <none>           <none>
rs-demo-6td6x   1/1     Running   0          4m43s   10.42.0.13   kubernetes   <none>           <none>
rs-demo-sj4hc   1/1     Running   0          4m43s   10.42.0.14   kubernetes   <none>           <none>
```

Vous noterez la présence de trois Pods dont le nom débute par celui du ReplicaSet responsable de leur création. Chaque Pod possède une adresse IP dédiée, permettant l'accès à la page hébergée par le conteneur `nginx.` 

Pour obtenir des informations détaillées sur les Pods du ReplicaSet, vous pouvez utiliser la commande `kubectl describe pod {{Pod_name}}` ou `kubectl describe rs {{RS_name}}` pour obtenir des détails spécifiques sur ce dernier.

Penser à supprimer votre ReplicaSet avant de passer à la suite :

```shell
kubectl delete rs rs-demo
```
```
replicaset.apps "rs-demo" deleted
```


## 6. Gestion des Deployments dans K8S

Un Deployment est un objet de niveau supérieur qui coordonne efficacement les Pods à travers les ReplicaSets. Il offre des avantages significatifs, notamment la capacité à fournir des mises à jour d'application de manière déclarative. Les Deployments offrent une gestion avancée des changements, permettant l'historisation des modifications et facilitant les opérations de `rollout` et de `rollback`, une fonctionnalité qui n'est pas présente dans les ReplicaSets. Ainsi, l'utilisation de Deployments simplifie la gestion des applications dans un cluster Kubernetes. Il est donc fortement recommandé d'opter pour l'utilisation de Deployments plutôt que directement pour les ReplicaSets.

### a. Mise en place d'un Deployment avec un ReplicaSet de trois Réplicas d'un Pod

Création du fichier `nginx-deploy.yaml` :

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.7.9
```

Vous pouvez observer que la structure précédente est conservée. Seul le champ `kind` spécifie que le type d'objet à créer est un Deployment.

Utilisez la commande suivant pour mettre en place le Deployment `nginx-deployment` :

```shell
kubectl apply -f nginx-deploy.yaml
```

Affichez l'inventaire de Deployment de votre cluster Kubernetes :

```shell
kubectl get deploy
```
```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           36s
```

La commande affiche des détails sur le déploiement `nginx-deployment`, indiquant que les trois répliques sont prêtes, à jour et disponibles, avec une durée de 36 secondes depuis la création.

Vous pouvez accéder à davantage d'informations en utilisant la commande suivante :

```shell
kubectl get deploy -o wide
```
```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE     CONTAINERS   IMAGES        SELECTOR
nginx-deployment   3/3     3            3           6m40s   nginx        nginx:1.7.9   app=nginx
```

Vous pouvez ainsi obtenir des détails étendus, notamment le nom du conteneur et l'image utilisée par les répliques du Pod. Vous pouvez observez la sélection des Pods basée sur le label `app:nginx`.

La commande `kubectl describe deploy nginx-deployment` permet d'afficher des informations détaillées sur le déploiement :

```shell
kubectl describe deploy nginx-deployment
```
```
Name:                   nginx-deployment
Namespace:              default
CreationTimestamp:      Fri, 08 Dec 2023 09:46:24 +0000
Labels:                 app=nginx
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=nginx
Replicas:               3 desired | 3 updated | 3 total | 3 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:  app=nginx
  Containers:
   nginx:
    Image:        nginx:1.7.9
    Port:         <none>
    Host Port:    <none>
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   nginx-deployment-7ddbcccf5b (3/3 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  10m   deployment-controller  Scaled up replica set nginx-deployment-7ddbcccf5b to 3
```

Les informations affichées comprennent les détails suivants :

> - Nom du déploiement : `nginx-deployment`.
> - Date de création : `Fri, 08 Dec 2023 09:46:24`
> - Label du déploiement : `app:nginx`.
> - Sélection des pods associés au déploiement : `Selector : app:nginx`.
> - Métadonnées du pod dans le template :
>     - Label du pod : `app:nginx`.
>     - Nom du conteneur : `nginx`.
>     - Image instanciée : `nginx:1.7.9`.
> - Informations sur le ReplicaSet :
>     - Répliques souhaitées : 3
>     - Répliques en cours de création.
>     - Répliques supprimées.
>     - Répliques nouvellement créées.

Affichez les Pods créés par le Deployment `nginx-deployment`:

```shell
kubectl get pods -o wide | grep -i "nginx-deployment"
```
```
nginx-deployment-7ddbcccf5b-sh92p   1/1     Running   0          18m   10.42.0.16   kubernetes   <none>           <none>
nginx-deployment-7ddbcccf5b-r5jjf   1/1     Running   0          18m   10.42.0.18   kubernetes   <none>           <none>
nginx-deployment-7ddbcccf5b-4tp5h   1/1     Running   0          18m   10.42.0.17   kubernetes   <none>           <none>
```

Affichez les ReplicaSets créés par le Deployment `nginx-deployment`:

```shell
kubectl get rs | grep -i "nginx-deployment"
```
```
nginx-deployment-7ddbcccf5b   3         3         3       19m
```

### b. L'Auto-Healing dans les Deployments

La fonctionnalité d'auto-healing, intégrée aux Deployments de Kubernetes, représente un mécanisme puissant de gestion de l'état désiré. En cas de défaillance ou de suppression d'un Pod, le Deployment détecte automatiquement cet état non désiré et déclenche des actions correctives. Cette capacité, souvent appelée auto-réparation, garantit que le Deployment maintient constamment le nombre spécifié de répliques en cours d'exécution, assurant ainsi la stabilité et la fiabilité des applications déployées.

Supprimez l'un des Pods de du Deployment :

```shell
kubectl delete pod nginx-deployment-7ddbcccf5b-4tp5h
```
```
pod "nginx-deployment-7ddbcccf5b-4tp5h" deleted
```

Affichez les détail de votre Deployment :

```shell
kubectl get pods -o wide | grep "nginx-deployment"
```
```
nginx-deployment-7ddbcccf5b-sh92p   1/1     Running   0          67m   10.42.0.16   kubernetes   <none>           <none>
nginx-deployment-7ddbcccf5b-r5jjf   1/1     Running   0          67m   10.42.0.18   kubernetes   <none>           <none>
nginx-deployment-7ddbcccf5b-4l5nb   1/1     Running   0          68s   10.42.0.20   kubernetes   <none>           <none>
```

Observez l'apparition d'un nouveau Pod, ici `nginx-deployment-7ddbcccf5b-4l5nb`.

### c. Historique des Versions avec Kubernetes

L'historique des versions dans Kubernetes offre une traçabilité précise des changements apportés aux déploiements, permettant un suivi efficace de l'évolution des applications déployées.

Actuellement, les Pods de votre Deployment utilisent la version 1.7.9 de l'image `nginx`.

```shell
kubectl get deploy -o wide | grep "nginx-deployment"
```
```
nginx-deployment   3/3     3            3           84m   nginx        nginx:1.7.9   app=nginx
```

Editez le fichier `nginx-deploy.yaml` et substituez la valeur `nginx:1.7.9` du champ `image` par `nginx:latest`.

```yml
    spec:
      containers:
      - name: nginx
        image: nginx:latest
```

Utilisez la commande `kibectl diff`pour visualiser les différences entre la configuration actuelle de votre Pod et la configuration spécifié dans le fichier `nginx-deploy.yaml`.

```shell
kubectl diff -f nginx-deploy.yaml
```
  
Vous pouvez observer que la version de l'image `nginx` devrait être mise à jour de 1.7.9 vers la dernière version disponible.

```
     spec:
       containers:
-      - image: nginx:1.7.9
+      - image: nginx:latest
```

Appliquez la mise à jour du Deployment :

```shell
kubectl apply -f nginx-deploy.yaml --record
```

Observez la mise à jour de l'image `nginx` utilisée :

```shell
kubectl get deploy -o wide
```
```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE    CONTAINERS   IMAGES         SELECTOR
nginx-deployment   3/3     3            3           101m   nginx        nginx:latest   app=nginx
```

Affichez l'historique du Deployment :

```shell
kubectl rollout history deployment/nginx-deployment
```

```
REVISION  CHANGE-CAUSE
1		  <none>
2         kubectl apply --filename=nginx-deploy.yaml --record=true
```

Vous pouvez observer la présence de deux révisions. La première, révision 1, correspond à la création initiale du Deployment, tandis que la deuxième, révision 2, correspond à la mise à jour.

Employez la fonction de `rollback` pour revenir en arrière et annuler la mise à jour, restaurant ainsi l'état précédent du Deployment.

```shell
kubectl rollout undo deployment/nginx-deployment --to-revision=1
```
```
deployment.apps/nginx-deployment rolled back
```

Vérifiez que la restauration a été effectuée en confirmant la version actuelle de l'image nginx utilisée par les Pods du Deployment.

```shell
kubectl get deploy -o wide
```
```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE    CONTAINERS   IMAGES        SELECTOR
nginx-deployment   3/3     3            3           3h2m   nginx        nginx:1.7.9   app=nginx
```

### d. Mise à l'échelle manuelle

Vous allez recourir à une commande impérative fin d'augmenter le nombre de répliques d'un Deployment.

Saisissez la commande suivante :

```shell
kubectl scale --replicas=4 deploy nginx-deployment
```

Cette commande permet d'ajuster le nombre de répliques du déploiement `nginx-deployment` à 4.

Observez les modifications du Deployment `nginx-deployment`:

```shell
kubectl get deploy | grep -i "nginx-deployment"
```
```
nginx-deployment   4/4     4            4           40m
```

```shell
kubectl get pods | grep -i "nginx-deployment"
```
```
nginx-deployment-7ddbcccf5b-sh92p   1/1     Running   0          41m
nginx-deployment-7ddbcccf5b-r5jjf   1/1     Running   0          41m
nginx-deployment-7ddbcccf5b-4tp5h   1/1     Running   0          41m
nginx-deployment-7ddbcccf5b-shfxq   1/1     Running   0          4m27s
```

  
Une autre approche aurait été de modifier directement le champ `replicas` dans le fichier `nginx-deploy.yaml`, suivi de l'application de cette mise à jour en utilisant la commande `kubectl apply`. C'est d'ailleurs la seule méthode pour réduire le nombre de répliques.

Utilisez la commande suivante pour repasser à une configuration à 3 répliques :

```shell
kubectl apply -f nginx-deploy.yaml
```
```
deployment.apps/nginx-deployment configured
```

Réutilisez les commandes précédentes pour observer les modification du Deployment.

Affichez les information détaillées concernant le Deployment et observez la section `Events`:

```shell
kubectl describe deploy nginx-deployment
```

```
Events:
  Type    Reason             Age    From                   Message
  ----    ------             ----   ----                   -------
  Normal  ScalingReplicaSet  48m    deployment-controller  Scaled up replica set nginx-deployment-7ddbcccf5b to 3
  Normal  ScalingReplicaSet  11m    deployment-controller  Scaled up replica set nginx-deployment-7ddbcccf5b to 4 from 3
  Normal  ScalingReplicaSet  3m20s  deployment-controller  Scaled down replica set nginx-deployment-7ddbcccf5b to 3 from 4
```

  
La commande `kubectl get events` permet d'afficher la liste des événements, fournissant des informations sur les activités récentes telles que les créations, mises à jour ou suppressions d'objets.

### e. Auto-Scaling Horizontal

L'objet `Horizontal Pod Autoscaler` de Kubernetes offre une solution automatisée pour ajuster dynamiquement le nombre de pods en fonction de la charge de travail. En surveillant les métriques définies, il peut augmenter ou diminuer le nombre de répliques de pods pour maintenir les performances et assurer une utilisation efficace des ressources, offrant ainsi une échelle horizontale automatisée en fonction des besoins de l'application.

  
> Afin d'explorer le comportement du `Horizontal Pod Autoscaler` (HPA), vous allez mettre en place un nouveau déploiement qui utilise une image personnalisée construite à partir de `php:5-apache`. Cette image intègre un fichier `index.php` contenant un script générant des calculs complexes à chaque requête client. Cette configuration vous permettra d'observer le mécanisme d'ajustement automatique du nombre de pods en fonction de la charge générée par les requêtes entrantes.


Création du fichier `apache-php.yaml` : 

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: php-apache
spec:
  selector:
    matchLabels:
      run: php-apache
  replicas: 1
  template:
    metadata:
      labels:
        run: php-apache
    spec:
      containers:
      - name: php-apache
        image: ppereira02/re20:latest
        ports:
        - containerPort: 80
        resources:
          limits:
            cpu: 500m
          requests:
            cpu: 200m
---
apiVersion: v1
kind: Service
metadata:
  name: php-apache
  labels:
    run: php-apache
spec:
  ports:
  - port: 80
  selector:
    run: php-apache
  
```

Ce fichier comprend deux parties distinctes pour un Deployment et un Service. Voici une description des champs de chaque partie :

**Déploiement (`Deployment`):**

- `apiVersion`: La version de l'API Kubernetes utilisée, ici `apps/v1`.
- `kind`: Le type d'objet Kubernetes, dans ce cas, `Deployment`.
- `metadata`: Les métadonnées associées au déploiement, comprenant le nom (`php-apache`).
- `spec`: La spécification du déploiement.
    - `selector`: Les sélecteurs pour déterminer quels pods sont gérés par ce déploiement.
        - `matchLabels`: Les étiquettes utilisées pour la sélection des pods (`run: php-apache`).
    - `replicas`: Le nombre de répliques souhaitées (1).
    - `template`: Le modèle pour créer de nouveaux pods.
        - `metadata`: Les métadonnées du pod.
            - `labels`: Les étiquettes du pod (`run: php-apache`).
        - `spec`: La spécification du pod.
            - `containers`: Les conteneurs à exécuter dans le pod.
                - `name`: Le nom du conteneur (`php-apache`).
                - `image`: L'image du conteneur (`ppereira02/re20:latest`).
                - `ports`: Les ports exposés par le conteneur (`80`).
                - `resources`: Les ressources allouées au conteneur.
                    - `limits`: Les limites de ressources, notamment pour le CPU (500m).
                    - `requests`: Les demandes de ressources, notamment pour le CPU (200m).

**Service (`Service`):**

- `apiVersion`: La version de l'API Kubernetes utilisée (`v1`).
- `kind`: Le type d'objet Kubernetes, dans ce cas, `Service`.
- `metadata`: Les métadonnées associées au service, comprenant le nom (`php-apache`).
- `spec`: La spécification du service.
    - `ports`: Les ports exposés par le service (ici, le port 80).
    - `selector`: Les sélecteurs pour déterminer quels pods sont gérés par ce service (ici, r`un: php-apache`).

Utilisez la commande ci-dessous pour créer à la fois le déploiement et le service :

```shell
kubectl apply -f apache-php.yaml
```
```
deployment.apps/php-apache created
service/php-apache created
```

A présent,  établissez un `HorizontalPodAutoscaler` qui ajuste automatiquement le nombre de répliques lorsque l'utilisation du CPU excède 50%, en veillant à maintenir un nombre de répliques compris entre 1 et 10.

```shell
kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=10
```

Affichez les informations concernant le HPA que vous venez de créer :

```shell
kubectl get hpa php-apache
```
```
NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/php-apache   0%/50%    1         10        1          84s
```

> Actuellement, la cible d'utilisation du CPU est fixée à 50%, mais l'utilisation actuelle est de 0%. Le nombre de répliques est actuellement 1, avec une plage autorisée entre 1 et 10.

Ouvrez un nouveau terminal et lancez la commande suivante :

```shell
kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
```

> Cela engendre la création d'un nouveau Pod qui fonctionne comme un client, générant des requêtes en boucle et induisant ainsi une augmentation de la charge sur le service Apache-PHP.

Revenez au terminal initial et observez l'évolution du HPA en temp réel avec la commande :


```shel
kubectl get hpa php-apache --watch
```
```
NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/php-apache   0%/50%    1         10        1          102s
php-apache   Deployment/php-apache   113%/50%   1         10        1          2m16s
php-apache   Deployment/php-apache   249%/50%   1         10        3          2m31s
php-apache   Deployment/php-apache   87%/50%    1         10        5          2m46s
php-apache   Deployment/php-apache   44%/50%    1         10        5          3m1s
php-apache   Deployment/php-apache   50%/50%    1         10        5          3m16s
php-apache   Deployment/php-apache   69%/50%    1         10        5          3m31s
php-apache   Deployment/php-apache   43%/50%    1         10        7          3m46s
php-apache   Deployment/php-apache   48%/50%    1         10        7          4m1s
php-apache   Deployment/php-apache   35%/50%    1         10        7          4m16s
```

> Dans cet exemple, on remarque que la cible d'utilisation du CPU fluctue, entraînant des ajustements automatiques du nombre de répliques pour maintenir les performances du service.

  
Utilisez la combinaison de touches `Ctrl + C` pour interrompre l'exécution du Pod qui effectue des requêtes vers votre service `apache-php`.

Vous noterez qu'après quelques instants, le HPA ajuste le nombre de pods à la baisse en réponse à la diminution de la charge CPU.

```
php-apache   Deployment/php-apache   0%/50%     1         10        7          9m2s
php-apache   Deployment/php-apache   0%/50%     1         10        6          9m17s
php-apache   Deployment/php-apache   0%/50%     1         10        6          10m
```

## 7. Gestion des Volumes dans Kubernetes

L'objet Volume de Kubernetes revêt une importance cruciale en raison de la nature éphémère des conteneurs. Les volumes permettent de résoudre les problèmes liés à la perte potentielle de données lors de la suppression ou de la recréation d'un conteneur, en particulier en cas de défaillance ou de mises à jour automatiques. Ces volumes assurent la persistance des données, même lorsque les conteneurs sont reconstruits, facilitant ainsi le partage et le stockage durable d'informations entre les conteneurs au sein d'un même Pod.

Kubernetes offre une polyvalence en matière de stockage, prenant en charge diverses technologies telles que les systèmes distribués comme SAN et NAS, ainsi que des solutions proposées par des fournisseurs tels qu'Amazon EBS et Microsoft AzureDisk. De plus, Kubernetes permet l'utilisation de répertoires du système hôte pour le stockage de données. 

Pour ce TP, nous explorerons les types de stockage `HostPath` et `PersistentVolume`.

### a. Les objets

**HostPath**

Le volume de type "hostPath" constitue une option de stockage dans Kubernetes, permettant à un conteneur d'accéder aux fichiers ou répertoires d'un système hôte et de les monter en tant que volume. Ce type de volume a été utilisé lors de la création du "pod" multi-conteneurs dans le TP.

Cependant, l'utilisation de ce type de volume requiert une vigilance particulière, car :

- Dans un cluster multi-nœuds, le dossier ou fichier monté doit être identique sur tous les nœuds du cluster.
- Les dossiers ou fichiers montés ne sont accessibles en écriture que par l'utilisateur root. Par conséquent, l'exécution du programme hébergé par un conteneur en tant que root est nécessaire pour pouvoir modifier les droits d'accès.

**PersistentVolume et PersistentVolumeClaim**

Les conteneurs, en raison de leur nature distribuée et dynamique, peuvent poser des problèmes de gestion et de configuration statique du stockage. Les volumes persistants résolvent ce défi en fournissant une API qui abstrait les détails de la manière dont le stockage est fourni et utilisé. Cette approche repose sur deux ressources essentielles : les PersistentVolumes et les PersistentVolumeClaims.

Les PV représentent l'espace de stockage disponible pour les PVC, qui sont des demandes spécifiant des caractéristiques telles que la taille et le mode d'accès. Ensemble, les PV et les PVC abstraient les détails liés à la fourniture et à l'utilisation du stockage.

### b. Mise en pratique 

1. Création d'un PV
Élaboration d'une configuration pour un PersistentVolume (PV) `local-pv.yaml` :

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: local-pv
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/pvdata"
```

Description du fichier :
> - `apiVersion`: `v1`.
> - `kind`: `PersistentVolume`.
> - `metadata`: 
> - `spec`: 
>     - `storageClassName`: Le nom de la classe de stockage associée au PV, ici `manual`.
>     - `capacity`: La capacité de stockage allouée, définie à 1 Go.
>     - `accessModes`: Les modes d'accès autorisés pour ce PV, ici `ReadWriteOnce` (lecture/écriture pour un seul noeud).
>     - `hostPath`: Le chemin sur le système hôte où le stockage sera effectivement provisionné, ici `/pvdata`.

Attention, si le chemin spécifié dans le champ `path` n'existe pas, Kubernetes ne le créera pas automatiquement, vous devrez le créer manuellement au préalable.

```shell
mkdir /pvdata
```

Lancez la création de PV `local-pv` :

```shell
kubectl apply -f local-pv.yaml
```
```
persistentvolume/local-pv created
```

Affichez la liste des PersistentVolumes du cluster :

```shell
kubectl get pv
```
```
NAME       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE
local-pv   1Gi        RWO            Retain           Available           manual                  81s
```

```shell
kubectl describe pv local-pv
```
```
Name:            local-pv
Labels:          type=local
Annotations:     <none>
Finalizers:      [kubernetes.io/pv-protection]
StorageClass:    manual
Status:          Available
Claim:
Reclaim Policy:  Retain
Access Modes:    RWO
VolumeMode:      Filesystem
Capacity:        1Gi
Node Affinity:   <none>
Message:
Source:
    Type:          HostPath (bare host directory volume)
    Path:          /pvdata
    HostPathType:
Events:            <none>
```

> Les utilisateurs du cluster ont maintenant la possibilité de réclamer jusqu'à 1 Go d'espace de stockage pour leurs Pods.

2. Création dun PVC
Pour tirer parti de cette nouvelle ressource de stockage, il est nécessaire de créer une revendication sous la forme d'un nouvel objet, un  `PersistentVolumeClaim`.

Création d'un fichier de configuration pour le PV `my-pvc.yaml`.

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

Description des champs du fichier :
> - `kind: PersistentVolumeClaim`: Spécifie le type d'objet.
> - `metadata`: Contient des métadonnées pour identifier de manière unique l'objet, telles que le nom de la revendication (`my-pvc`).
> - `spec`: Définit les spécifications de la revendication.
>     - `storageClassName: manual`: Indique la classe de stockage utilisée pour la revendication.
>     - `accessModes: [ReadWriteOnce]`: Spécifie le mode d'accès au volume, dans ce cas, lecture-écriture exclusivement pour un nœud.
>     - `resources`: Définit les ressources requises par la revendication.
>         - `requests`: Indique la quantité de stockage demandée,(`1Gi`).

Tapez la commande suivante pour créer le PVC `my-pvc` :

```shell
kubectl apply -f my-pvc.yaml
```
```
persistentvolumeclaim/my-pvc created
```

Affichez le status du PVC :

```shell
kubectl get pvc my-pvc
```
```
NAME     STATUS   VOLUME     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
my-pvc   Bound    local-pv   1Gi        RWO            manual         37s
```

  
La sortie de la commande  fournit des informations suivantes :
> - `NAME`: Le nom de la revendication (`my-pvc`).
> - `STATUS`: Indique l'état actuel de la revendication. `Bound` signifie que la revendication est liée à un volume persistant.
> - `VOLUME`: Le nom du volume persistant associé à la revendication (`local-pv`).
> - `CAPACITY`: La capacité du volume persistant (`1Go`).
> - `ACCESS MODES`: Le mode d'accès au volume, ici `RWO` (ReadWriteOnce), indiquant un mode de lecture-écriture exclusivement pour un nœud.
> - `STORAGECLASS`: La classe de stockage associée (`manual`).
> - `AGE`: L'âge de la revendication depuis sa création, ici, `37s`.

Après la création du « PersistentVolumeClaim », le plan de contrôle Kubernetes recherche un `PersistentVolume` répondant aux critères spécifiés dans la revendication. Si un `PersistentVolume` adéquat portant le même `StorageClass` est identifié, la revendication est liée à ce volume.
### c. Deployment  intégrant un PVC en tant que volume de stockage
Dans cet exemple, nous allons revisiter le scénario du pod multi-conteneur du début du TP pour mettre en place un Deployment nommé `deploy-with-pv` avec les caractéristiques suivantes :

- Le Deployment utilise un volume persistant nommé `depl-pv`, qui est partagé entre les deux conteneurs `nginx`et `debian`.
- Ce volume persistant est défini par une revendication de volume persistant (PVC) nommée `my-pvc`.
- Le volume `depl-pv` est monté dans les deux conteneurs à des chemins de montage différents mais correspondant au même stockage sous-jacent.

> **nginx** : Sert le contenu HTML depuis le répertoire `/usr/share/nginx/html`, qui est monté sur un volume persistant (`depl-pv`).
> 
> **debian** : Exécute un script en boucle qui écrit la date actuelle dans un fichier nommé `index.html` toutes les 2 minutes. Ce script utilise le même volume persistant (`depl-pv`), monté sur le chemin `/html`.


Créez le fichier `nginx-pv-deploy.yaml`.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deploy-with-pv
  labels:
    app: nginx
spec:
  replicas: 1
  selector:
    matchLabels: 
      app: nginx
  template:
    metadata:
      labels: 
        app: nginx
    spec:
      volumes: 
        - name: depl-pv
          persistentVolumeClaim: 
            claimName: my-pvc    
      containers:
      - name: nginx
        image: nginx:latest
        volumeMounts:
          - mountPath: "/usr/share/nginx/html"
            name: depl-pv
      - name: debian
        image: debian:latest
        volumeMounts:
          - mountPath: "/html"
            name: depl-pv
        command: ["/bin/sh", "-c"]
        args:
          - while true; do
              date >> /html/index.html;
              sleep 120;
           done
```

Description :

Cette section du fichier spécifie la configuration d'un volume appelé `depl-pv`, lié à la revendication persistante `my-pvc` pour le stockage dans le Deployment.

```yaml
    spec:
      volumes: 
        - name: depl-pv
          persistentVolumeClaim: 
            claimName: my-pvc 
```

Cette partie indique que le volume `depl-pv` est monté dans le chemin du système de fichiers `/usr/share/nginx/html` du conteneur `nginx`.

```yaml
      - name: nginx
        image: nginx:latest
        volumeMounts:
          - mountPath: "/usr/share/nginx/html"
            name: depl-pv
```

Cette partie indique que le volume `depl-pv` est monté dans le chemin du système de fichiers `html` du conteneur `debian`.

```yaml
     - name: debian
        image: debian:latest
        volumeMounts:
          - mountPath: "/html"
            name: depl-pv
```

Appliquez la configuration pour créer le nouveau Deployment :

```shell
kubectl apply -f nginx-pv-deploy.yaml
```
```
deployment.apps/deploy-with-pv created
```

### d. Validation du fonctionnement des Volumes

Utilisez la commande `kubectl get deploy -o wide`pour trouver l'adresse IP du Deployment `deploy-with-pv` puis, utilisez `curl` pour afficher le contenu de la page servie par `nginx` :

Exemple :

```shell
curl -s --noproxy '*' 10.42.0.48
```
```
Fri Dec  8 14:36:43 UTC 2023
Fri Dec  8 14:38:43 UTC 2023
Fri Dec  8 14:40:43 UTC 2023
Fri Dec  8 14:42:43 UTC 2023
Fri Dec  8 14:44:43 UTC 2023
Fri Dec  8 14:46:43 UTC 2023
Fri Dec  8 14:48:43 UTC 2023
Fri Dec  8 14:50:43 UTC 2023
Fri Dec  8 14:52:43 UTC 2023
Fri Dec  8 14:54:43 UTC 2023
```

Vérifiez que les Pods utilisent bien le répertoire local de l'hôte définie lors de la création du PV `local-pv` :

```shell
cat /pvdata/index.html
```
```
Fri Dec  8 14:36:43 UTC 2023
Fri Dec  8 14:38:43 UTC 2023
Fri Dec  8 14:40:43 UTC 2023
Fri Dec  8 14:42:43 UTC 2023
Fri Dec  8 14:44:43 UTC 2023
Fri Dec  8 14:46:43 UTC 2023
Fri Dec  8 14:48:43 UTC 2023
Fri Dec  8 14:50:43 UTC 2023
Fri Dec  8 14:52:43 UTC 2023
Fri Dec  8 14:54:43 UTC 2023
```

==Supprimez tous les Deployments créés jusqu'à présent avant de passer à la suite du TP.==

## 8. Gestion de Services de Kubernetes

Dans Kubernetes, un objet Service est un moyen d'exposer une application exécutée sur un ensemble de Pods en tant que service réseau stable. Il fournit une abstraction permettant d'accéder aux Pods sans se soucier de leur emplacement exact dans un cluster. Un Service peut être utilisé pour exposer une application à l'intérieur du cluster (Service ClusterIP), à l'extérieur du cluster (Service NodePort ou LoadBalancer), ou même à l'extérieur du cluster avec une adresse IP statique (Service ExternalName). Il agit comme un point d'entrée réseau pour accéder aux fonctionnalités offertes par les Pods sous-jacents.

Au cours de ce TP, nous explorerons les services de type ClusterIP et NodePort.

### a. L'objet  Service de type ClusterIP 

Au cours de cette étape, vous allez mettre en place un service de type `ClusterIP` pour exposer le service web fourni par les Pods identifiés avec le label `app:nginx` sur le port 8080/TCP.

Créez le fichier de configuration `nginx-cip-svc.yaml` pour définir l'objet `nginx-service`.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: ClusterIP
  selector:
    app: nginx
  ports:
  - port: 8080
    targetPort: 80
    name: nginx-cluster-ip
```

Description des champs :
> - `kind`: `Service`.
> - `metadata`:
> 	- `name`: Nom du service (`nginx-service`)
> - `spec`:
>     - `type`: `ClusterIP`.
>     - `selector`: Spécifie les Pods associés au service en fonction de leurs labels (`app: nginx`).
>     - `ports`: Définit les ports exposés par le service, avec les informations suivantes :
>         - `port`: Port du service (`8080`).
>         - `targetPort`: Port auquel le trafic est redirigé vers les Pods associés (`80`)
>         - `name`: Nom du port du service, défini comme `nginx-cluster-ip`.
	
Créez le service avec la commande suivante :

```shell
kubectl apply -f nginx-cip-svc.yaml
```
```
service/nginx-service created
```

Observez les informations relatives au service que vous venez de créer :

```shell
kubectl get svc nginx-service
```
```
NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
nginx-service   ClusterIP   10.43.242.155   <none>        8080/TCP   56s
```

### b. Mise en place d'un Deployment associé au Service ClusterIP
  
Maintenant, vous allez instancier un nouveau Deployment avec les spécifications suivantes :
- Un seul conteneur qui exécute l'image `nginx`.
- Le pod est étiqueté avec le label `app:nginx`.
- Le conteneur `nginx` écoute sur le port 80/TCP.
- 3 répliques du pod doivent être déployées.

Création du fichier `nginx-deploy.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```

Création du Deployment `nginx-deployment` :

```shell
kubectl apply -f nginx-deploy.yaml
```
```
deployment.apps/nginx-deployment created
```

Affichez les information concernant le Deployment : 

```shell
kubectl get deploy -o wide
```
```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE   CONTAINERS   IMAGES   SELECTOR
nginx-deployment   3/3     3            3           56s   nginx        nginx    app=nginx
```

Affichez les Endpoints (Points de terminaison) associés au service `nginx-service`.

```
kubectl get endpoints nginx-service
```
```
NAME            ENDPOINTS                                   AGE
nginx-service   10.42.0.49:80,10.42.0.50:80,10.42.0.51:80   15m
```

>  Ces points de terminaison indiquent les adresses IP et les ports des Pods du service, permettant ainsi aux clients d'accéder au service.

Affichez la liste des Pods créés par le Deployment : 

```shell
kubectl get pods -o wide | grep nginx-deployment
```
```
nginx-deployment-55f598f8d-lpg9t   1/1     Running   0          7m7s   10.42.0.50   kubernetes   <none>           <none>
nginx-deployment-55f598f8d-tlg2j   1/1     Running   0          7m7s   10.42.0.51   kubernetes   <none>           <none>
nginx-deployment-55f598f8d-6kl54   1/1     Running   0          7m7s   10.42.0.49   kubernetes   <none>           <none>
```

Testez le fonctionnement du service avec la commande `curl` et l'adresse IP de service `nginx-service` :

```shell
curl -s --noproxy '*' http://10.43.242.155:8080
```
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Schéma illustrant le parcours des requêtes clients internes dans le cluster.

![[K3_03.png | 400]]

### c. Le Service de type NodePort

Un service de type `NodePort` permet d'exposer une application sur un port statique sur chaque nœud du cluster, offrant ainsi aux clients externes la possibilité d'accéder à l'application via l'adresse IP de n'importe quel nœud du cluster en utilisant le port spécifié.

Reprenez le fichier de configuration du Service `nginx-service`créé dans la section précédente et apportez les modifications suivantes `:`
- Remplacez la valeur du champ `type`par `NodePort`.
- Ajoutez le champ `nodePort` pour spécifier le port sur lequel le service sera exposé sur chaque nœud du cluster.
- Changer le nom du port.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
  - port: 80
    nodePort: 30001
    targetPort: 80
    name: nginx-np
```

> La création d’un Service NodePort engendre automatiquement la création d’un service ClusterIp. Par convention, on donne la même valeur aux champs port et `targetPort`.

> Par défaut, la plage de ports utilisée par les services de type `NodePort` est de 30000 à 32767

Appliquez les changements de votre service : 

```shell
kubectl apply -f nginx-cip-svc.yaml
```
```
service/nginx-service configured
```

Affichez les détails de votre service `nginx-service`et observez la colonne `TYPE` et le port exposé dans la colonne `PORT(S)`:

```shell
kubectl get svc nginx-service
```
```
NAME            TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
nginx-service   NodePort   10.43.242.155   <none>        80:30001/TCP   45
```

Obtenez les informations détaillées :

```shell
kubectl describe svc nginx-service
```
```
Name:                     nginx-service
Namespace:                default
Labels:                   <none>
Annotations:              <none>
Selector:                 app=nginx
Type:                     NodePort
IP Family Policy:         SingleStack
IP Families:              IPv4
IP:                       10.43.242.155
IPs:                      10.43.242.155
Port:                     nginx-np  80/TCP
TargetPort:               80/TCP
NodePort:                 nginx-np  30001/TCP
Endpoints:                10.42.0.49:80,10.42.0.50:80,10.42.0.51:80
Session Affinity:         None
External Traffic Policy:  Cluster
Events:                   <none>
```

Testez l'accès à page web hébergée par `nginx` en utilisant l'adresse IP de votre noeud K3S :

```shell
curl -s --noproxy '*' http://10.23.13.1:30001
```
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Contrairement à Docker, Kubernetes ne permet pas d'exposer facilement les applications à l'extérieur sur des ports standards, car les services sont conçus pour être plus abstraits et indépendants des nœuds individuels du cluster.

Les principales options pour exposer une application sur des ports standard sont :

1. **Service de type LoadBalancer** : Utilisé dans les environnements cloud, il permet d'exposer un service sur un port externe (standard) et de distribuer le trafic entrant entre plusieurs pods de manière équilibrée. Lorsqu'un service de type `LoadBalancer` est créé, le fournisseur de cloud provisionne automatiquement un équilibreur de charge externe et lui attribue une adresse IP publique ou privée, assurant ainsi l'accès externe aux applications déployées dans le cluster Kubernetes. 

2. **Service de type Ingress** : Utilisé pour gérer l'accès HTTP/HTTPS externe aux services dans un cluster Kubernetes via des contrôleurs d'Ingress comme Nginx Ingress Controller ou Traefik. Il permet de centraliser et de gérer les règles de routage pour plusieurs services et de les exposer via des ports standard. L'Ingress agit comme une couche d'abstraction qui définit les règles de routage pour diriger le trafic entrant vers les services appropriés en fonction des chemins d'URL, des hôtes, etc. 

### d. Le service Ingress

**Objectif** : créer un Ingress nommé `nginx-ingress` qui redirige le trafic entrant pour le domaine `re20.local` vers un service Nginx.

Traefik est pré-configuré comme contrôleur d'Ingress par défaut dans K3s. Vous n'aurez donc pas besoin de l'installer avec des outils comme HELM par exemple.

**Mise en oeuvre :**

Supprimez tous ce que vous avez créé jusqu'à présent avec les commandes suivantes :

```shell
kubectl delete deploy --all
kubectl delete svc --all
kubectl delete hpa --all
kubectl delete pvc --all
kubectl delete vc --all
```

Choisissez un emplacement de votre choix pour créer un répertoire que vous nommerez selon vos préférences. Ce nouveau répertoire sera utilisé pour héberger les trois fichiers manifestes à venir.


1. Création d'un déploiement : `depl.yml`

> Ce déploiement crée une instance du serveur web Nginx.
> Il spécifie le déploiement de l'image Nginx avec un seul réplica.
> Le réplica écoute sur le port 80 pour les requêtes HTTP entrantes.
> Les labels sont utilisés pour identifier et sélectionner ce déploiement lors de la création de services ou d'Ingress

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

2. Création d'un service de type ClusterIP : `svc.yml`

> Ce service expose le déploiement Nginx à l'intérieur du cluster Kubernetes.
> Il utilise une IP ClusterIP pour permettre aux autres services internes de communiquer avec le service Nginx.
> Les labels sont utilisés pour sélectionner les pods associés au service.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx
spec:
  type: ClusterIP
  ports:
  - port: 80
    targetPort: 80
  selector:
    app: nginx
```

3. Création d'un service ingress : `ingress.yml`

> Cet ingress définit les règles de routage pour le trafic entrant vers le cluster.
> Il redirige le trafic du domaine re20.local vers le service Nginx précédemment créé.
> Les labels sont utilisés pour sélectionner le service de destination du trafic entrant.

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: nginx-ingress
  annotations:
    kubernetes.io/ingress.class: "traefik"
    traefik.frontend.rule.type: PathPrefixStrip
spec:
  rules:
  - host: re20.local # par en-tête d'hôte
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: nginx
            port:
              number: 80
```

Déplacez-vous dans votre répertoire, puis saisissez la commande suivante pour créer les objets définis dans les trois fichiers :

```shell
kubectl apply -f .
```

Assurez-vous que vos différents objets ont été créés :

```shell
kubectl get all
```

Testez le fonctionnement depuis le terminal de votre poste de travail avec la commande suivante en utilisant l'adresse IP de votre master K3s :

```shel
curl -H "Host:re20.local" 10.23.x.y
```

> L'option -H "Host:re20.local" est utilisé pour simuler l'accès au domaine re20.local, étant donné que nous n'avons pas d'enregistrement DNS correspondant à ce domaine.

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Vous pouvez supprimer les objets que vous venez de créer avec la commande :

```shell
kubectl delete -f .
```