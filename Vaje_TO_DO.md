# Vaje

## Vaja 1:
- [x] Izberite si projekt, na katerem boste delali tekom semestra.
- [ ] Pripravite osnutek mikrostoritev, ki jih boste implementirali, in predvidenih povezav med njimi. Upoštevajte, da so za različne povezave lahko primerni različni tipi komunikacije. Razmislite o storitvah, ki jih mora ponujati vaša aplikacija.
- [x] Pripravite si razvojno okolje. 
- [x] Kreirajte organizacijo in repozitorije na GutHub-u.
- [x] Implementirajte vsaj dve osnovni mikrostoritvi, ki komunicirata med sabo.

## Vaja 2:
### Zasnova arhitekture
- [ ] Pripravite seznam primerov uporabe vaše mikrostoritvene aplikacije in zapišite/zarišite arhitekturo, ki naj vsebuje:
    - [ ] shemo mikrostoritev in njihovih interakcij in
    - [ ] primere sporočil in zahtevkov, ki jih bo obdelovala aplikacija.
- [ ] Identificirajte nekaj kompleksnejših zahtevkov, pri obdelavi katerih bodo sodelovale vsaj tri mikrostoritve.
- [x] Zasnovano arhitekturo predstavite asistentu na vajah in objavite v enega izmed repozitorijev. Priporočena je uporaba ločenega repozitorija za dokumentacijo.
- [x] Zasnovana arhitektura predstavlja prvo iteracijo in jo bomo skozi semester še izpopolnjevali in dopolnjevali.

### Priprava slik Docker
- [x] Mikrostoritvam, ki ste jih začeli implementirati v prvi nalogi, dodajte definicijo za gradnjo slik Docker – datoteko Dockerfile. Datoteka naj se nahaja v repozitoriju posamezne mikrostoritve. Pri definiciji datoteke uporabite ustrezno izvorno sliko, v vašo sliko pa zapakirajte samo najnujnejše artefakte, potrebne za izvajanje mikrostoritve. 
- [x] Slike objavite na portalu Docker Hub.

## Vaja 3:
### Vzpostavitev zvezne integracije
Z uporabo Travis CI (ali druge storitve po vaši izbiri) vzpostavite cikel zvezne integracije, ki naj:
- [x] vse spremembe iz GitHub veje master prevede in zapakira (build),
- [ ] izvede teste enot (unit testing) – teste bomo dodali v nadaljevanju semestra,
- [x] ustvari novo sliko Docker,
- [x] objavi sliko na portalu Docker Hub.

Zvezna integracija vam mora delovati skozi celoten semester na vseh repozitorijih in je ena izmed osnovnih zahtev za uspešno opravljene vaje.

### Upravljanje s konfiguracijo
Seznanite se z naslednjimi koncepti upravljanja konfiguracije, ki jih bomo uporabljali v nadaljevanju semestra (ter preverjali na zagovorih, kolokvijih in izpitih):
- [x] Konfiguracija mikrostoritev z uporabo okoljskih spremenljivk.
    - [x] Kdaj uporabimo ta način konfiguracije?
    - [x] Kakšna je podpora s strani izbranega mikrostoritvenega ogrodja? Zakaj je pomembna?
    - [X] Kakšna je prioriteta okoljskih spremenljivk v izbranem mikrostoritvenem ogrodju in zakaj?
- [x] Definiranje okoljskih spremenljivk ob zagonu vsebnikov Docker.
    - [x] Preučite in testiranje načine definiranja okoljskih spremenljivk v okolju Docker.
    - [x] Vaše mikrostoritve zaženite v okolju Docker in pri tem konfiguracijske vrednosti, specifične za zagon v določenem okolju (npr. konfiguracija povezave na bazo), definirajte z uporabo okoljskih spremenljivk.


Pripravite načrt upravljanja s konfiguracijo v vaši aplikaciji. Pri tem:
- [ ] identificirajte vso konfiguracijo vaše aplikacije,
- [x] ločite implementacijo in konfiguracijo – konfiguracijo naj bo mogoče spreminjati brez ponovnega prevajanja in nameščanja mikrostoritve,
- [x] predvidite uporabo različnih virov konfiguracije, npr. konfiguracijske datoteke, okoljske spremenljivke, konfiguracijski strežnik...,
- [x] na smiselnem primeru podprite dinamično rekonfiguracijo storitve, npr. z uporabo konfiguracijskega strežnika.
- [x] V ogrodju KumuluzEE lahko uporabite razširitev KumuluzEE Config.

## Vaja 4:
### Odkrivanje storitev
Odkrivanje storitev v okolju Docker.

- [x] V primeru zagona mikrostoritve in pripadajoče podatkovne baze kot dveh vsebnikov Docker je potrebno v mikrostoritvi določiti naslov vsebnika s podatkovno bazo. Zaradi dinamične narave okolja Docker ne uporabimo IP naslova vsebnika, temveč vgrajen mehanizem za odkrivanje vsebnikov.
- Preučite in preizkusite
    - [x] odkrivanje vsebnikov z uporabo koncepta Docker network (npr. docker network ls) in imenom vsebnika ter
    - [x] odkrivanje vsebnikov znotraj namestitve Docker compose (primer).


Zasnova in implementacija odkrivanja storitev v vaši aplikaciji.
- [x] Zasnujte odkrivanje storitev v vaši aplikaciji. Posodobite implementacijo vaših obstoječih mikrostoritev tako, da bodo vsi klici med posameznimi mikrostoritvami implementirani s pomočjo odkrivanja storitev. Statično kodiranje povezav med mikrostoritvami ni sprejemljivo.
- [x] Posameznim storitvam določite imena, ki jih bomo uporabljali za odkrivanje storitev. Odkrivanje storitev bomo vzpostavili ob namestitvi mikrostoritev na Kubernetes, ki uporablja podobne koncepte kot Docker.

### Kubernetes
- [x] Ustvarite si račun pri poljubnem ponudniku oblačnih storitev. Izberite ponudnika, ki ponuja že nameščeno okolje Kubernetes. Nekaj možnih ponudnikov:
    - [x] Azure (Azure for Education).
        - [x] egistracija brez kreditne kartice, 100 € kreditov.
    - [x] Google Cloud Platform
        - [x] Pri registraciji je zahtevana kreditna kartica, 300 € kreditov, možno kreirati več trial računov enega za drugim.
    - [x] OpenShift
    -    [x] Registracija brez kreditne kartice
    - [x] Uporabite lahko tudi npr. DigitalOcean, AWS, IBM Cloud ...
- [x] Po kreiranju računa, vam ponudniki tipično ponudijo orodja in niz ukazov, s katerimi si lokalno skonfiguriramo orodje kubectl.
- [x] Ustvarite namestitvene datoteke za vaše namestitve in storitve. Dodajte jih v git repozitorij k pripadajoči storitvi.
- [x] Pri namestitvah uporabite docker slike, ki vam jih CI cikel objavlja v repozirotiju.
- [x] Ustrezno konfigurirajte Kubernetes storitve (services). Prikažite uporabo različnih tipov storitev (npr. ClusterID, NodePort, ...). Nekaj vaših storitev naj bo začasno dostopnih na javnem IP naslovu. V naslednjih tednih jih bomo izpostavili skozi ingress proxy.
- [x] Ustrezno implementirajte odkrivanje storitev.
- [x] Za zunanje storitve, npr. podatkovne baze, lahko uporabite storitve, ki jih ponuja izbrani ponudnik računalništva v oblaku.

## Vaja 5:
### Ingress
- [x] Konfigurirajte ingress proxy, tako da bodo vse vaše mikrostoritve javno dostopne preko enega naslova.
- [x] Uporabite lahko ingress, ki je nameščen na vašem oblaku, ali pa namestite poljuben ingress controler, npr. NGINX Ingress Controller

### API za preverjanje vitalnosti in Kubernetes Liveness Probes
- [x] V vaše storitve dodajte API za preverjanje vitalnosti.
- [x] Uporabite lahko KumuluzEE Health.
- [x] Implementirajte vsaj dve kontroli zdravja.
- [x] API za preverjanje zdravja naj vrača ustreze HTTP status kode, da bo skladen s Kubernetes Liveness Probes.
- [x] V namestitvene datoteke Kubernetes za namestitve (deployments) dodajte Liveness Probes in Readiness Probes
- [x] Simulirajte bolno storitev (npr. z dinamično konfiguracijo ali POST zahtevkom) in opazujte, ali jo Kubernetes na novo zažene.

### Zbiranje metrik
- [x] Storitvam dodajte končno točko, na kateri izpostavite nekaj metrik.
- [x] Uporabite lahko KumuluzEE Metrics.

## Vaja 6:
### Kubernetes in dnevniške datoteke
- [x] Kubernetes ponuja osnovne mehanizme za delo z dnevniki.
- [x] Preglejte dokumentacijo ukaza kubectl logs.
- [x] Izpišite dnevniške datoteke vseh podov neke namestitve (deployment).

### Implementacija centralnega beleženja dnevnikov
- [x] Dnevniške datoteke (logs) vaših mikrostoritev shranjujte v sistem za centralizirano beleženje dnevnikov.
    - [x] V vaše mikrostoritve lahko dodate orodje za beleženje dnevnikov, ki bo dnevnike pošiljalo v sistem za centralizirano beleženje dnevnikov. Uporabite lahko KumuluzEE Logs.
    - [x] Uporabite lahko orodja, ki na Kubernetesu berejo izpise podov in jih posredujejo v sistem za zbiranje dnevniških zapisov.
- [x] Uporabite lahko trial račun na logit.io.
    - [x] Za uporabo z Log4j2 uporabite appender tipa TCP.
- [x] Storitev naj vsakemu dnevniškemu zapisu doda tudi kontekstne podatke (ime storitve, verzija, okolje...). V Log4j2 lahko za ta namen implementirate interceptor. Dodajte tudi unikaten identifikator zahtevka, ki naj enolično označuje en zahtevek, ki se lahko izvede na več mikrostoritvah.
- [x] Vaše mikrostoritve naj beležijo vse vstope in izstope v metode posameznih končnih točk REST.
- [x] V orodju za pregled dnevnikov pripravite tri zanimive poizvedbe po dnevnikih (npr. izpis dnevnikov določene mikrostoritve, izpis vseh vstopov v določeno metodo, ...)
    - [x] Primer: marker.name: ENTRY || marker.name: EXIT

## Vaja 7:
### Izolacija in toleranca napak
- [ ] Simulirajte napako pri enem izmed klicev med dvema mikrostoritvama (npr. mikrostoritev se registrira na napačnem naslovu ali na napačnih vratih, mikrostoritev vrača nepravilno formatirane podatke ...).
- [ ] Cilj te naloge je omejiti širjenje vpliva napak posamezne mikrostoritve na celotno aplikacijo.
- [ ] Pri implementaciji odpornosti na napake si lahko pomagate z razširitvijo KumuluzEE Fault Tolerance.
- [ ] Pripravite ustrezen nadomestni mehanizem (fallback), ki se bo prožil v primeru napake na klicani mikrostoritvi.
- [ ] Pri implementaciji odpornosti na napake lahko uporabite časovnik (timeout).
- [ ] Uporabite prekinjevalec toka (circuit breaker). Pripravite demo, v katerem prikažete različna stanja prekinjevalca toka (odprto, pol-odprto, zaprto).
- [ ] Ponovno simulirajte napako na eni izmed mikrostoritev in opazujte delovanje aplikacije.

### Uporaba zunanjih (3rd party) API-jev
- [x] V vašo aplikacijo vključite kak zunanji API.
- [x] API-je lahko najdete na portalu RapidAPI.
- [x] Uporabite lahko npr. tudi Amazon Rekognition.

### Opomba: spletni in/ali mobilni vmesnik
- [x] Ne pozabite pripraviti preprostega uporabniškega (spletnega in/ali mobilnega) vmesnika za vašo aplikacijo.
- [x] Uporabniški vmesnik naj zajema nekaj preprostih zaslonov, s katerimi boste demonstrirali delovanje aplikacije (npr. nalaganje slike, pregled vseh slik uporabnika, prikaz ene slike skupaj z komentarji ...).
- [x] Uporabniški vmesnik naj bo preprost, poudarek naj bo na prikazu implementiranih funkcionalnosti vaše mikrostoritvene aplikacije.

## Vaja 8:
### Sporočilni in pretočni sistemi
- [ ] V vašo aplikacijo (smiselno) vključite sporočilni sistem ali platformo za pretočne dogodke.
    - [ ] V pomoč naj vam bo arhitektura aplikacije, ki smo jo zasnovali na začetku semestra.
    - [ ] S sporočili oz. dogodki lahko na primer prožite procesiranje ali analizo slik oz. zvočnih posnetkov.
- [ ] Uporabite lahko rešitev as a service, ali pa potrebno platformo namestite sami.

## Vaja 9:
### Samodejno skaliranje
- [ ] Vašim namestitvam ustrezno konfigurirajte samodejno skaliranje (Horizontal Pod Autoscaling).
- [ ] Simulirajte povečano obremenitev.
- [ ] Generirate lahko večjo količino prometa iz neke druge (za ta namen vzpostavljene) gruče Kubernetes.
- [ ] Simulirajte promet na tri različne končne točke REST, za katere pričakujete, da bi v realni postavitvi aplikacije prejemale največ prometa.
- [ ] Opazujte potek samodejnega skaliranja ob povečevanju in zmanjševanju obremenitve.
- [ ] Pripravite demo, ki ga boste pokazali na zagovoru.

## Napredni komunikacijski protokoli
- [ ] V vašo mikrostoritveno aplikacijo vključite GrahpQL, gRPC ali asinhrone REST klice.


# Zagovori projektov bodo potekali v dveh tednih:
    - 6. do 10. januar
    - 13. do 17. januar
- Vsaka skupina mora na prvem tednu zagovorov zagovoriti vsaj (cca) polovico nalog.
- Na zagovore prihajajte v terminih, ki jih imate vpisane na urniku.
- Na zagovoru bomo ocenjevali:
    - Arhitekturno zasnovo aplikacije in kvaliteto rešitve danega problema.
    - Vsebinsko ustreznost razvitih mikrostoritev. Pripravite vsaj pet demonstrativnih primerov uporabe razvite aplikacije, pri obravnavi katerih sodeluje več mikrostoritev.
    - Razumevanje konceptov, ki so bili izpostavljeni v navodilih nalog.
    - Implementacijo in razumevanje zahtev iz nalog (npr. konfiguracija, odkrivanje storitev, Kubernetes, preverjanje vitalnosti, beleženje dnevnikov ...).
    - Število razvitih mikrostoritev. Vsak član skupine mora razviti vsaj tri mikrostoritve.
- Na zagovore prihajajte pripravljeni:
    - Vaše mikrostoritve naj bodo nameščene na Kubernetesu.
    - Imejte pripravljeno izvorno kodo vaših mikrostoritev.
    - Vse koncepte iz nalog in njihovo implementacijo morate razumeti in jo znati razložiti.