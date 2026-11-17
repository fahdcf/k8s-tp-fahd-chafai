# TP 4 Kubernetes

Déploiement de whoami sur un cluster kind à trois nœuds sous Windows avec Docker Desktop. Travaux pratiques de Fahd Chafai, filière Génie logiciel, ENSA Al Hoceima, 2026/2027.

## Fichiers du TP

- [Compte rendu PDF](Compte_rendu_TP4_Kubernetes_Fahd_Chafai.pdf) avec les captures sélectionnées et les réponses aux cinq questions.
- [kind-config.yaml](kind-config.yaml) définit le plan de contrôle, les deux workers et la publication du port 30080.
- [pod.yaml](pod.yaml) décrit le Pod NGINX autonome.
- [whoami.yaml](whoami.yaml) décrit le Deployment et le Service NodePort.
- [Historique des révisions](evidence/rollout-history.txt) et [journal des sondes HTTP](evidence/whoami-availability.txt) consignent les mesures du TP.

## Résultats

Le Service distribue les requêtes entre les Pods whoami. Le Deployment remplace un Pod supprimé et passe de trois à six répliques. Pendant la mise à jour vers v1.11, huit sondes HTTP consécutives échouent avant la reprise des réponses. Lors du test de l’image v9.99, cinq Pods v1.11 restent disponibles et le journal ne relève aucun échec jusqu’après le rollback. Celui-ci restaure six répliques v1.11.
