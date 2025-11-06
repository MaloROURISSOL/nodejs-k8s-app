# NODEJS-K8S-APP Questions

### Consultez le rapport de couverture dans coverage/lcov-report/index.html. Quel est le taux de couverture ?

![Coverage Report](./img/2025-11-0309.52.14.png)

Le rapport de couverture indique un taux de 93,54%.

## Docker

### curl http://localhost:3000 :
```
malorourissol@Mac-mini-de-Malo nodejs-k8s-app % curl http://localhost:3000
{"message":"Bienvenue sur mon API Node.js!","version":"1.0.0","visits":1,"hostname":"unknown","timestamp":"2025-11-03T09:35:56.299Z"}% 
```

### curl http://localhost:3000/health :
```
{"status":"ok","timestamp":"2025-11-03T09:35:56.299Z"}
```

```
malorourissol@Mac-mini-de-Malo nodejs-k8s-app % curl -X POST http://localhost:3000/api/calculate \
  -H "Content-Type: application/json" \
  -d '{"a": 10, "b": 5}'
{"sum":15,"product":50,"difference":5,"quotient":2}% 
```

## GitHub Actions
Tous les tests passent avec succès.

![GitHub Actions](./img/Capture%20d’écran%202025-11-06%20à%2009.01.35.png)

## Exercice 1 : Observer le comportement des pods
Lorsque l'on supprime un pod (ici à la main), Kubernetes crée automatiquement un nouveau pod pour maintenir le nombre de réplicas défini dans le déploiement. Ils se recréent vite.

- Ready : Indique si le pod est prêt à recevoir du trafic. Pret à etre intégré dans le cluster.
- Running : Indique que le pod est en cours d'exécution. Le pod est actif et fonctionne.

## Exercice 2 : Tester le Rolling Update
Oui les deux versions coexistent pendant la mise à jour. On peut le voir avec la commande `kubectl get pods` où les pods des deux versions sont présents simultanément.

## Exercice 3 : Tester l'autoscaling
Lors de forte charge, le nombre de pods augmente pour gérer la demande. Lorsque la charge diminue, le nombre de pods revient à la normale. La création de pods est instantanée et la suppression est progressive (300s soit 5min si tout va bien).
Après la charge, le nombre de pods est redescendu à 2.

## Exercice 4 : Ajouter une nouvelle fonctionnalité
