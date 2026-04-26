# Proiect Practic 12 - Simulator de Atac și Apărare pe o Rețea Virtuală 
## Universitatea Politehnica Timișoara - Facultatea de Automatică și Calculatoare - Securitatea Informațiilor și a Sistemelor Cibernetice (SISC)
### Brei Paul - SISC - Anul 1 - Gr 1.1

<br>

#### Informații Generale
Acest repository reprezintă atât implementarea practică a proiectului, cât și documentația pentru acesta. Documentația necesară se găsește în acest fișier README, dar și în jurnalul atacatorului, care poate fi găsit în fișierele din repository.

Proiectul are scopul de a oferi mediul virtual necesar pentru simularea unui atac de mișcare laterală, folosind docker compose. Acesta include un container pentru atacator, care rulează Kali Linux, trei victime care rulează Ubuntu, două rețele, cea exterioară și cea interioară, și un sistem de detecție a intruziunilor (IDS) Suricata. 

Atacul de mișcare laterală presupune câștigarea accesului la o victimă vulnerabilă dintr-o rețea privată de către un atacator care, în mod normal, nu ar avea acces la aceasta. Odată ce atacatorul a preluat accesul la stația din rețeaua internă, el se poate mișca prin aceasta, câștigând accesul la orice mașină vulnerabilă din rețea, descoperind astfel informații confidențiale. 

În contextul proiectului, scopul atacatorului este să ajungă la victima finală, unde va găsi „Date Super Confidențiale”. Inițial, atacatorul se află în rețeaua externă (10.0.0.0/24), însă are acces la victima 1, care se situează în ambele rețele. El nu poate vedea sau intercaționa cu celelate victime din rețeaua internă în acest punct. Astfel, odată ce are accesul la mașina victimei 1, poate căuta informații, mișcându-se prin rețeaua internă (192.168.10.0/24) pentru a ajunge la victima finală. Utilizatorul poate folosi jurnalul atacatorului pentru lansarea atacului, fiecare pas incluzând comenzile care trebuie rulate și explcațiile necesare.

IDS-ul Suricata poate fi folosit pentru observarea mesajelor de alertă cauzate de câteva comenzi folosite pentru lansarea atacului. Acesta are doar rol de prezenta informații și nu este integrat cu un sistem de prevenire a intruziunilor. 

<br>

#### Pași pentru rularea proiectului
Se recomandă ca proiectul să fie rulat într-un mediu bazat pe Linux, cu Docker instalat.

1. Descărcați arhiva .zip a repository-ului și extrageți fișierele într-un folder separat pe mașina dumneavoastră.
2. Deschideți un terminal și navigați până în folder-ul în care ați dezarhivat proiectul.
3. Folosoți comanda `sudo docker-compose up --build -d` pentru a crea și construi containerele docker. Acest lucru poate dura câteva minute.
4. Actualizați sistemul de detecție a intruziunilor Suricata, folosind comanda `sudo docker exec -it ids_node suricata-update`.
5. După ce ați actualizat Suricata, rulați comanda `sudo docker restart ids_node`, pentru a se actualiza regulile.
6. Așteptați câteva secunde, și consultați output-ul comenzii `sudo docker logs ids_node`. Dacă în output nu se regăsește linia „Engine Started”, rulați din nou comanda pănâ când aceasta apare.
7. Pentru a vedea mesajele Suricata, deschideți un nou terminal în paralel în același folder, și rulați comanda `tail -f ids/logs/fast.log`. În momentul n care se detectează o activitate suspectă, va apăarea un nou mesaj în acest fișier de log-uri. Puteți să păstrați terminalul cu procesul deschis în paralel pentru a vedea modul în care mesajele apar în timp real, sau să consultați fișierul de log-uri oricând folosind aceeași comandă.
8. Acum puteți accesa container-ul atacatorului, utilizând comanda `sudo docker exec -it attacker_node /bin/bash`.
9. Mai apoi, puteți folosi jurnalul atacatorului pentru a vedea pașii necesari lansării atacului!
10. Pentru a închide containerele, utilizați comanda `sudo docker-compose down`.

