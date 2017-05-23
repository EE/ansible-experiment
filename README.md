# aplikacje.gov.pl – Eksperyment Ansible
## Cel eksperymentu
Eksperyment polega na stworzeniu architektury (playbooka i ról) [Ansible](https://www.ansible.com/) umożliwiającej uruchomienie dockerowego kontenera z serwerem Apache, który serwuje plik index.html z tytułem konfigurowalnym przez użytkownika.

**Celem eksperymentu jest wydanie rekomendacji dotyczącej wykorzystania programu Ansible w procesie konfiguracji Instancji.**


#### Pytania eksperymentalne:

1. Jak będzie wyglądać intergracja Ansible z webowym UI konfiguratora?
    - Jakie są różnice pomiędzy powyższym sposobem integracji a modelem aktualnie realizowanym (który jest nakładką na docker/docker-compose)?
    - Czy i jak zmienią się aktualnie używane w konfiguratorze modele?
2. Czy Ansible będzie się umiał zająć zarządzaniem użytkownikami w BD?
3. Wykorzystując docker-compose mamy problem z tym, że modyfikacja jednego serwisu wymaga restartu wszystkich. (docker-compose down; create new compose file; docker-compose up; ) Czy Ansible jest pod tym względem lepsze?
4. Jak można się komunikować z Ansible? Pisze sie skrypty w plikach czy jest jakieś inne API?
5. Czy plik parametryzacyjny (*parameters.json*) można zastąpić odpowiednim Playbookiem bądź Rolą?

#### Efekty:

1. Decyzja odnoście użycia programu Ansible przy tworzeniu konfiguratora instancjii.
2. Zarys części architektury konfiguratora wykorzystującej Ansible (w przypadku pozytywnej decyzji).

## Przebieg eksperymentu

### O Ansible (teoretycznie)

Ansible jest narzędziem umożliwiającym automatyzację i orchiestryzację zadań związanych ze zdalnym zarządzaniem serwerami.

Szczególnie warto zwrócić uwagę na dwie jego cechy:

- Deklaratywne definiowanie pożądanego stanu systemu (*CO* zamiast *JAK*)
- Idempotencję (wiele wywołań idempotentnej funkcji ma taki sam efekt jak jej pojedyncze wywołanie). Oznacza to, że jeżeli oczekiwany przez użytkownika stan jest już na serwerze osiągnięty, stan tego serwera nie ulegnie zmianie.

Zalety Ansible:

- Czystość:
    - Brak agentów
    - Brak bazy danych
    - Brak dodatkowego oprogramowania
    - Brak skomplikowanych uaktualnień
- YAML
    - Przyjazna i przejrzysta składnia (*YAML ain't a markup language*)
    - Nie wymaga doświadczenia programistycznego
- Wbudowane security
- Modularność => rozszerzalność

#### Architektura

#### Inwentarz

#### Playbooki

#### Role

### Struktura repozytorium

## Wnioski

### Rekomendacja

## Odtworzenie eksperymentu

#### Wymagania

- [Ansible](http://docs.ansible.com/ansible/intro_installation.html)
- [Vagrant](https://www.vagrantup.com/intro/index.html)

#### Proces

1. Sklonować repozytorium:
2. przejść do katalogu: `cd sciezka/do/repo`
3. w konsoli wpisać: `vagrant up`
4. w konsoli wpisać: `ansible-playbook webserver.yml`
5. otworzyć w przeglądarce adres `192.168.33.20`