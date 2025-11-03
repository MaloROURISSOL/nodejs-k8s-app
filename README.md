# NODEJS-K8S-APP Questions

## Consultez le rapport de couverture dans coverage/lcov-report/index.html. Quel est le taux de couverture ?

![Coverage Report](./img/2025-11-0309.52.14.png)

Le rapport de couverture indique un taux de 93,54%.

## Docker

curl http://localhost:3000 :
```
malorourissol@Mac-mini-de-Malo nodejs-k8s-app % curl http://localhost:3000
{"message":"Bienvenue sur mon API Node.js!","version":"1.0.0","visits":1,"hostname":"unknown","timestamp":"2025-11-03T09:35:56.299Z"}% 
```

curl http://localhost:3000/health :
```
{"status":"ok","timestamp":"2025-11-03T09:35:56.299Z"}
```

```
malorourissol@Mac-mini-de-Malo nodejs-k8s-app % curl -X POST http://localhost:3000/api/calculate \
  -H "Content-Type: application/json" \
  -d '{"a": 10, "b": 5}'
{"sum":15,"product":50,"difference":5,"quotient":2}% 
```