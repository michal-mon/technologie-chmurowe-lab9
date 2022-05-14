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
      Plik "Dockerfile.Phpfmp" powstał w oparciu o <a href="https://hub.docker.com/_/phpmyadmin">dokumentację na Dockerhub</a> oraz <a href="https://wiki.alpinelinux.org/wiki/Nginx_with_PHP">wpis na wiki.alpinelinux.org</a>.<br/>Na bazie obrazu "alpine" zostaje wykonana instalacja modułów PHP (wersja 7) oraz podstawowa konfiguracja zmiennych środowiskowych, zdefiniowanie, jakich wolumenów ma używać zbudowany obraz oraz uruchomienie PHP.
    </li>
    <li>
      <h4>Dockerfile.Nginx</h4>
      Plik "Dockerfile.Nginx" powstał na bazie obrazu "alpine", na którym została wykonana instalacja serwera "nginx", stworzenie katalogu "/www", zmiana uprawnień do "/www" oraz "/var/lib/nginx" (flaga -R powoduje działanie rekursywne) oraz uruchomienie serwera "nginx".
    </li>
  </ul>
</p>
<h3>Plik "docker-compose.yml":</h3>
<p></p>
<h3>Sprawdzenie poprawności działania:</h3>
