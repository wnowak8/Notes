<h1>Python & Threads</h1>
Proces wykonywania zadań przy pomocy puli wątków:

1. Utworzenie puli wątków, wywołując konstruktor ThreadPoolExecutor() .
2. Przesłanie zadania i uzyskanie obiektu Future, wywołując submit() lub map() .
3. Poczekanie na uzyskanie wyników po ukończeniu zadań (opcjonalnie).
4. Zamknięcie puli wątków, wywołując shutdown() .

![Schemat](https://i0.wp.com/superfastpython.com/wp-content/uploads/2021/11/ThreadPoolExecutor-Life-Cycle.png?w=384&ssl=1)

ThreadPoolExecutor rozszerza klasę Executor i po wywołaniu zwróci obiekty Future.

- **Executor** : Klasa nadrzędna dla ThreadPoolExecutor, która definiuje podstawowe operacje cyklu życia dla puli.
- **Future** : obiekt zwracany podczas przesyłania zadań do puli wątków, które mogą zostać ukończone później.

Klasa Executor definiuje trzy metody używane do kontrolowania naszej puli wątków; są to: submit() , map() i shutdown() .

- submit() : Wysyła funkcję do wykonania i zwraca przyszły obiekt.
- map() : Zastosuj funkcję do iteracji elementów.
- shutdown() : Wyłącza executor.

Executor jest uruchamiany podczas tworzenia klasy i musi zostać zamknięty jawnie przez wywołanie funkcji shutdown() , która zwolni wszystkie zasoby przechowywane przez executor.
```python
# create a thread pool with 10 worker threads
executor = ThreadPoolExecutor(max_workers=10)
```
Funkcje submit() i map() służą do przesyłania zadań do Executora w celu wykonania asynchronicznego.

Funkcja map() działa tak samo jak wbudowana funkcja map() i służy do zastosowania funkcji do każdego elementu w obiekcie iterowalnym, takim jak lista. W przeciwieństwie do wbudowanej funkcji map() , każde zastosowanie funkcji do elementu nastąpi asynchronicznie, a nie sekwencyjnie.
```python
# perform all tasks in parallel
results = pool.map(my_task, my_items) # does not block
# perform all tasks in parallel
# iterate over results as they become available
for result in executor.map(my_task, my_items, timeout=5):
	# wait for task to complete or timeout expires
	print(result)
```
Funkcja submit() pobiera funkcję, a także wszelkie argumenty, i wykona ją asynchronicznie, chociaż wywołanie zwraca natychmiast i udostępnia obiekt Future.
```python
# submit a task with arguments and get a future object
future = executor.submit(my_task, arg1, arg2) # does not block
# submit a task with no arguments and get a future object
future = executor.submit(my_task) # does not block
# get the result from a future
result = future.result() # blocks
```
Różnica między submit(), map():
- map() zwraca iterator nad obiektami, a nie nad obiektami Future. 
- map() zwraca wyniki w kolejności, w jakiej zadania zostały przesłane, a nie w kolejności ich ukończenia. 
  
Obiekt Future udostępnia szereg przydatnych funkcji do sprawdzania stanu zadania, takich jak: cancelled() , running() i done() w celu określenia, czy zadanie zostało anulowane, jest aktualnie uruchomione, czy też zakończyło wykonywanie.

- cancelled() : Zwraca True , jeśli zadanie zostało anulowane przed wykonaniem.
- running() : Zwraca True , jeśli zadanie jest aktualnie uruchomione.
- done() : Zwraca True , jeśli zadanie zostało zakończone lub anulowane

Obiekt Future zapewnia również dostęp do wyniku zadania za pośrednictwem funkcji result() . Jeśli wyjątek został zgłoszony podczas wykonywania zadania, zostanie on ponownie zgłoszony podczas wywoływania funkcji result() lub można uzyskać do niego dostęp za pomocą funkcji exception().

- result() : Uzyskaj dostęp do wyniku uruchomienia zadania. 
- exception() : Uzyskaj dostęp do każdego wyjątku zgłoszonego podczas wykonywania zadania.

<h4>Domyślna łączna liczba wątków = (łączna liczba procesorów) + 4 </h4>
Aby pula wątków automatycznie wywoływała funkcję po zakończeniu zadania należy dołączyć wywołanie zwrotne do obiektu Future dla zadania za pomocą funkcji add_done_callback() .

add_done_callback() : Dodaj funkcję zwrotną do zadania, które ma zostać wykonane przez pulę wątków po zakończeniu zadania.

Czekanie do momentu otrzymania pierwszego resultatu z puli wątków wykonuje się przy pomocy stałej FIRST_COMPLETED przekazanej do argumentu „ return_when ”.
```python
# wait until we get the first result
done, not_done = wait(futures, return_when=concurrent.futures.FIRST_COMPLETED)
```
Alternatywnie możemy poczekać na zakończenie wszystkich zadań poprzez stałą ALL_COMPLETED .
```python
# wait for all tasks to complete
done, not_done = wait(futures, return_when=concurrent.futures.ALL_COMPLETED)
```
Istnieje również opcja oczekiwania na pierwszy wyjątek poprzez stałą FIRST_EXCEPTION .
```python
# wait for the first exception
done, not_done = wait(futures, return_when=concurrent.futures.FIRST_EXCEPTION)
```
Funkcja as_completed() zwróci obiekty Future dla zadań po ich zakończeniu w puli wątków.Często używa się funkcji as_completed() w pętli nad listą obiektów Future tworzonych podczas wywoływania submit; na przykład:
```python
# iterate over all submitted tasks and get results as they are available
for future in as_completed(futures):
	# get the result for the next completed task
	result = future.result() # blocks
```
Po wykonaniu wszystkich zadań możemy zamknąć pulę wątków, co zwolni każdy wątek i wszelkie zasoby, które może posiadać (np. przestrzeń stosu wątków).
```python
# shutdown the thread pool
executor.shutdown() # blocks
```
Funkcja shutdown() będzie domyślnie czekać na zakończenie wszystkich zadań w puli wątków, zanim zwróci.
To zachowanie można zmienić, ustawiając argument „ czekaj ” na False podczas wywoływania funkcji shutdown() , w którym to przypadku funkcja zwróci się natychmiast. 
```python
# shutdown the thread pool
executor.shutdown(wait=False) # does not blocks
```
Możemy również poinstruować pulę, aby anulowała wszystkie zadania w kolejce, aby zapobiec ich wykonaniu. Można to osiągnąć, ustawiając argument „ cancel_futures ” na True . Domyślnie zadania w kolejce nie są anulowane podczas wywoływania funkcji shutdown() .
```python
# cancel all queued tasks
executor.shutdown(cancel_futures=True) # blocks
```
Tworzenie puli wątków za pomocą menedżera kontekstu:
```python
...
# create a thread pool
with ThreadPoolExecutor(max_workers=10) as pool:
	# submit tasks and get results
	# ...
	# automatically shutdown the thread pool...
# the pool is shutdown at this point
```
[Source](https://superfastpython.com/threadpoolexecutor-in-python/)