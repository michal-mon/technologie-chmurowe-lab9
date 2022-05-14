<h1>Sprawozdanie - Technologie Chmurowe Laboratorium 9</h1>
<h2>Autor: Michał Moń</h2>
<h3>Ogólny opis repozytorium:</h3>
<p>Repozytorium zawiera foldery:
  <ul>
    <li>"Nginx" - znajduje się w nim plik "Dockerfile.Nginx" służący do zbudowania obrazu serwera nginx oraz plik konfiguracyjny "nginx.conf" (na bazie: <a href="https://wiki.alpinelinux.org/wiki/Nginx_with_PHP">link</a>)</li>
    <li>"www" - znajduje się nim plik "index.php", który służy do wyświetlenia informacji o konfiguracji PHP, link: <a href="https://www.php.net/manual/en/function.phpinfo.php">phpinfo</a></li>
  </ul>
  Poza tymi folderami w repozytorium znajduje się też plik "Dockerfile.Phpfmp", który służy do zbudowania obrazu PHP oraz "docker-compose.yml", który definiuje usługi (oraz ich konfigurację) dla aplikacji Docker.
</p>
<h3>Pliki "Dockerfile":</h3>
<p>
  <ul>
    <li>
      <h4>Dockerfile.Phpfmp</h4>
      Plik "Dockerfile.Phpfmp" powstał w oparciu o <a href="https://wiki.alpinelinux.org/wiki/Nginx_with_PHP">wpis na wiki.alpinelinux.org</a>.<br/>Na bazie obrazu "alpine" zostaje wykonana instalacja modułów PHP (wersja 7) oraz podstawowa konfiguracja zmiennych środowiskowych, zdefiniowanie, jakich wolumenów ma używać zbudowany obraz oraz uruchomienie PHP.
    </li>
    <li>
      <h4>Dockerfile.Nginx</h4>
      Plik "Dockerfile.Nginx" powstał na bazie obrazu "alpine", na którym została wykonana instalacja serwera "nginx", stworzenie katalogu "/www", zmiana uprawnień do "/www" oraz "/var/lib/nginx" (flaga -R powoduje działanie rekursywne) oraz uruchomienie serwera "nginx".
    </li>
  </ul>
</p>
<h3>Plik "docker-compose.yml":</h3>
<p>Plik "docker-compose.yml" zawiera opis utworzenia usług składających się na stos LEMP (Linux, Nginx, MySQL, PHP) oraz phpMyAdmin. Serwer "nginx" został zbudowany na podstawie pliku "Dockerfile.Nginx" znajdującego się w katalogu "Nginx". Nasłuchuje na porcie 3000 (nie został wykorzystany port 6666, ze względu na problem z blokowaniem tego portu przez przeglądarki). Jest przyłączony do sieci "backend" oraz "frontend".<br/>Usługa "phpfmp" została zbudowana na podstawie pliku "Dockerfile.Phpfmp". Jest przyłączona do sieci "backend".<br/>Usługa "mysql" powstała na bazie oficjalnego <a href="https://hub.docker.com/_/mysql">obrazu na Dockerhub</a>. Posiada skonfigurowane zmienne środowiskowe, tj.: login, hasło, bazę danych, oraz hasło "root". Jest przyłączona zarówno do sieci "backend" jak i "frontend".<br/>Usługa "phpmyadmin" powstała na bazie <a href="https://hub.docker.com/_/phpmyadmin">obrazu na Dockerhub</a>. Jest przyłączona do sieci "backend". Dodatkowo zostały skonfigurowane zmienne środowiskowe "PMA_HOST" - zdefiniowanie hosta (w tym przypadku MySQL) oraz "PMA_PORT" - zdefiniowanie portu serwera (w tym przypadku 3306).</p>
<h3>Sprawdzenie poprawności działania:</h3>
<h4>Polecenie "docker compose -f docker-compose.yml up</h4>
<img src="/img/1_1.png">
<img src="/img/1_2.png">
<h4>Polecenie "docker ps -a"</h4>
<img src="/img/2.png">
<h4>Wyświetlenie konfiguracji PHP (serwer Nginx)</h4>
<img src="/img/3.png">
<h4>Pomyślne logowanie do phpMyAdmin</h4>
<img src="/img/4.png">
<img src="/img/5.png">
  
  
