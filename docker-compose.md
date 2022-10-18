docker-compose -f docker-compose.yml up -d
sudo docker build -t <nazwa_obrazu> .


distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
   
   sudo docker exec -it posture_detection_container bash
docker create-stworzenie kontenera bez wywoływania komendy startowej z obrazu. Należy rozumieć jako jedynie zarezerwowanie części zasobów hosta i skopiowanie plików z obrazu na wycinek dysku przeznaczony dla owego kontenera. W odpowiedzi otrzymany jego unikalny numer id. Kontener nie zostanie uruchomiony.

docker start-uruchomienie istniejącego już kontenera, opcja -a przekierowuje logi z kontenera do naszego okna

docker ps-wyświetlenie listy kontenerów obecnych na naszym komputerze, opcja --all/-a wyświetla również wyłączone kontenery

docker run-wywołana jedynie z nazwą obrazu uruchomi kontener, korzystając z komendy startowej podanej w obrazie. Jeżeli jednak podamy kolejny argument tuż po nazwie obrazu, ten argument nadpisze domyślną komendę z obrazu i to ona zostanie uruchomiona tuż po starcie kontenera. Składnia wtedy będzie wyglądała następująco <docker run image-name startup_command>

docker run<=> docker create,a potem docker start

docker images- lista obrazów

docker rm-usunięcie pojedyńczych kontenrów

docker system prune-komenda czyszcząca nasz system z nieużywanych kontenerów, obrazów i kilku innych używanych przez Dockera zasobów

docker logs-wyświetlenie wszystkich logów, które zostały wygenerowane w konkretnym kontenerze

docker stop-grzeczne wyłączenie kontenera. Po wywołaniu tej komendy wraz z podaniem id kontenera Docker wyśle do działającego procesu tzw. sygnał SIGTERM. Jeżeli proces jest przygotowany na obsłużenie tego sygnału, może wykonać dodatkowe czynności, zanim zostanie wyłączony, np. zapis plików. Ma jednak na to tylko 10 sekund. Jeżeli po tym czasie proces będzie nadal aktywny, zostanie wykonana komenda docker kill

docker kill-natychmiastowe wyłączenie kontenera bez podejmowania żadnych innych akcji. Wywoływane wraz z id kontenera

 docker exec-uruchomienie kolejnego procesu wewnątrz kontenera, zazwyczaj wykonywana jest wraz z flagą -it (złożenie dwóch osobnych flag -i oraz -t), dzięki czemu będziemy otrzymywać do naszego terminala ładnie sformatowane logi pochodzące z nowo uruchomionego procesu oraz uzyskamy możliwość wprowadzania komend wewnątrz tego procesu (to, co napiszemy na klawiaturze, zostanie przekierowane do terminala wewnątrz kontenera). Składnia polecenia: docker exec -it containerId komenda
 **wyjście CTRL+D**
 
 kontenery to instancje obrazów, a obrazy definiuje się w Dockerfilu
 
 docker build -t <nazwa obrazu> . - budowanie obrazu z Dockerfila
 -t -otagowanie obrazu
 .- bieżący katalog
 docker run -p 8000:8080  -v <path do projektu>:<path do katalogu roboczego w kontenere> <nazwa obrazu>
 -p  <port na kom><port z Dockerfila> -który port na kom ma odpwidać portowi zdefiniowanemu w Dockerfilu
 
