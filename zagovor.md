# Zagovor

## O projektu
- Ime: Data-platforma
- Mikrostoritve:
    - data-upload
    - data-storage-service
    - data-catalog
    - data-analyzer (ni še dokončano)
- Github:
    - https://github.com/rso-projekt-leon

## Zasnova arhitekture
- Primeri uporabe:
    - Shranjevanje podatkov (dataseti) v oblačni storitvi za različne uporabnike.
    - Osnovni povzetek analize za prenesene datasete.
    - Možnost natančnejše analize z enostavnim vmesnikom
- Shema: 
    - [arhitektura](https://www.draw.io/?state=%7B%22folderId%22:%221FV8YL8B8_Ef2b7yIGWNsNjmWiNn2vZap%22,%22action%22:%22create%22,%22userId%22:%22105336244406619544036%22%7D#G1AAB4un1cQ9VzXBFwSL10mpTZnAfOjURd)

## Priprava slik Docker
- dockerfile (razvoj, test in produkcija)
- Dockerhub: https://hub.docker.com/

## Vzpostavitev zvezne integracije
- https://travis-ci.org/

## Upravljanje s konfiguracijo
- uporabljen config file, evn, in etcd
- ETCD demo na data_upload
    - https://35.195.92.163/data-catalog/v1/etcdtest
    - preko terminla lahko spremenimo vrednost in se updata

## Odkrivanje storitev
- network docker-compose
- kubernetes, preko imen mikrostoritve

## API za preverjanje vitalnosti in Kubernetes Liveness Probes
- data-upload implemtacija
- https://35.195.92.163/data-upload/health/live
- https://35.195.92.163/data-upload/health/ready
- test:
    - spremeni /data-upload/health-demo-status na False

## Zbiranje metrik
- https://35.195.92.163/data-upload/metrics

## Kubernetes in dnevniške datoteke
- [Logging Architecture](https://kubernetes.io/docs/concepts/cluster-administration/logging/)
- `kubectl logs <pod name>`

## Implementacija centralnega beleženja dnevnikov
- Logiranje nastavljeno na: **data-upload (INFO)**
- Filebeat pod bere zapise iz podov ostalih mikrostoritev
- Centralno beleženje dnevnikov [tukaj](https://logit.io/a/e47f14b4-f928-447a-8ea8-7ae23db57d84)
    - filter: kubernetes.pod.name: data-upload-deployment-6bd8c5b56c	

## Izolacija in toleranca napak
- nič posebnega, razen sporgramirnao tako da ne neha delati vse

## Uporaba zunanjih (3rd party) API-jev
- Amazon S3

## Opomba: spletni in/ali mobilni vmesnik
- frontend zaganan lokalno

## Samodejno skaliranje
- ni še implemenitrano

## Napredni komunikacijski protokoli
- plan na data-analysis (FastAPI framework) - native GraphQL podpora


