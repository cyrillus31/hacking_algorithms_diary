#system-design
#interview 

![[Pasted image 20241019212842.png]]

![[Pasted image 20241019212904.png]]

Miro board:
	https://miro.com/app/board/uXjVLZJa5Mg=/
#### Главный принцип по проектироваю Rest API 
API  не должно содержать глаголов
- api/v2/elements
- ~~api/v2/getElements~~

#### throughput, response time, latency
1.  throughput 
	- Пропускная способность системы
	- Сколько запросов вернется за n времени
2. response time
	1. Сколько занимает полный цикл в системе от захода до возврата
3. latency
	1. ???

#### Почему микросервисы лучше монолитов
Монолит не всегда плох!!!

- Разделение ответственности и изоляция
- Быстрее деплой 
- БД разделяем и повышваем устойчивость и скорость.
		- у каждого свое БД
		- Выше безопасность, так как сервисы не могут спокойно ходить в другие БД

#### Scaling
1. Вертикальное - увеличение мощности
2. Горизонтальное - увеличиваем количество
3. Функциональная декомпозиция - распиливание одной системы на более мелкие (микросервисы). Паттерн strangler fig.

#### Какие виды деплоя?
- Canary deployment: есть 3 пода, 2 остаются со старой версией, а 1 выкатывается с новым функционалом. 
- rolling создается новый ReplicaSet, который постепенно вытесняет старый.
- Blue/Green: одна версия крутится в prod, а вторая на test контуре тестирутеся
	vestion: blue
	docker tag blue

 
 Load Balancer HAProxy && Nginx

Open System Intercommunication Model
Подход, котоырй описывает движение данных по сети с верхнего у ровня до нижнего.

![[Pasted image 20241005131320.png]]

![[Pasted image 20241005131337.png]]

Вариации termination/paththrew

#### Масштабирование БД
Partitioning - в рамках одной БД
Sharding - в рамках разных БД

#### Обеспечение отказоустойчивости БД
Replication


Как будем реплицировать данные:
- По какому-то полю, напрмер updated_at
![[Pasted image 20241005132149.png]]

Какие виды репликаций существуют?
![[Pasted image 20241005132823.png]]
- Синхронная (обновляем запись в двух местах, на основной и на реплике)
- Асинхронная
- Семисинхронная

#### HOT-STANDBY
Если падает мастер, то реплика становится мастером.
![[Pasted image 20241005132717.png]]
Leader election алгоритм выбора реплики.

![[Pasted image 20241005132959.png]]
relational
non-relational
column-oriented
blob/object storage
time-series
graph database
search engines
key-value
high-availability key-value

#### Для чего нужны поисковые движки?
- Elasticsearch - движо, который хранит данные и позволяет делать быстрый поиск по тексту. Днанные хранятся в JSON-подобном формате
- Sphinx
- Используется inverted index
- Хорошо масштабируется в распределенной системе на множество nodes
- В отличие от GIN/GIST индексов в постгресе быстро обновляются и хорошо работают на больших кусках текста.


#### Caching
![[Pasted image 20241005134128.png | 500]]
Снижает нагрузку на сервис.
- Можем сначала писать в кэш, а потом в базу
- Можем сначала писать в базу, а потмо в кэш
Eviction (замещение) стратегии кэша: fifo, lifo, lru, mru, lfu ... 

Cache invalidation
![[Pasted image 20241005134823.png]]

##### Event driven подход (очереди)
- topic based
- queue based
![[Pasted image 20241005134922.png]]

#### Kafka
![[Pasted image 20241005135027.png]]

#### Как оценивается система с точки зрения бизнеса
SLA -  service level agreement (обязательство, что сервис будет доступен определенное время в году, а другое время (секунды, часы) будет недоступен). Измеряется в девятках (что это значит?)
SLO - цели команд, чтобы выполнить соглашение
![[Pasted image 20241005135345.png]]


На что обратить внимание
1. Авторизайия
2. Как ведут себя сабскрайберы в распределенных системах?
3. Облака

## 1. Собрать требования
На что следует обратить внимание в начале собеседования:
	- как делать (функциональные требования)
	- какие метрики (RPS разделяется на чтение и на запись) (нефункциональные)
	- десктоп или мобилка
	- клиент-сервер (API) или сервер-сервер (API, может быть gRPC и очеред)
	- observability
	- критичность системы (mission critical или нет)


![[Pasted image 20241019123821.png]]

## 2. Накидать простой дизайн системы 
![[Pasted image 20241019124044.png]]

- Можно начать с: **клиент + балансер + монолит. А дальше начинаем менять**.


# Задача на проектирование по avito
![[Pasted image 20241019124258.png]]

Classified - это сайты, где размещаются обьявления (как avito).

![[Pasted image 20241019124546.png]]
DAU - daily active users
MAU - max active users
RPS - 1 : 100 на каждые 100 запросов 

![[Pasted image 20241019125012.png]]

![[Pasted image 20241019125200.png]]

При расчете RPS можно учитывать сезонность, но это редко.

## Storage
![[Pasted image 20241019125755.png]]

![[Pasted image 20241019125900.png]]

Круто разбивать на внутренние и внешние апишки.

![[Pasted image 20241019130012.png]]




Балансер делает простую балансировку на L3 и L4 или умную балансировку на L7. 
**Service mash**
API gateway вешает trace. Jaeger.

## Auth
![[Pasted image 20241019130907.png]]

Аутентификация - мы понимаем, что такой пользователь есть.
Авторизация - что у пользователя есть права


## DNS
![[Pasted image 20241019131120.png]]
VPN - proxy
Load Balancer - reverse-proxy

Как синхронизация базы происходит?


## Resharding

![[Pasted image 20241019131520.png]]



# Проектирование!


- client - balancer - server - db
- geodns
![[Pasted image 20241019132110.png]]

### Bottleneck
SPoF


Я выбор технологию **ПОТОМУ ЧТО Я С НЕЙ РАБОТАЛ**.

CDC - capture data change (для инвалидации кэша)

Retry (3), backOff(exponential или рандом) - чтобы повторить запросы, которые упали из за большого потока сообщений.

Поиск по Elastic.

![[Pasted image 20241019135725.png]]


Почему не стоит использовать Elastic как основную базу - чтобы отволился только поиск, а монго остался. 

Graceful degradation (когда отламывается только часть функционала).

Blog storage/ object storage (s3) - для хранения объектов, картинок. 

CQRS pattern - when we split a system into read and write (when avatar of a user on an external server).

CDN - технология, подход, который позволяет нам уменьшить лейтенси для статических данных.
	POP - points of presence

### Sync of geo clusters
Синхранизация между кластерами через Topic based queue (Kafka).


### Observability
1. logs: fluentbit/fluentD (сгребает логи, процесси и скидывает в elastic search)
2. metrics
	- techincal: CPU, RAM, Disk
	- business: RPS, DAU, MAU
3. alerts
	- healthcheck
	- PromQL (если больше 4 400-ок за минуту, то улетает звонок на телефон)
	- tracing (когда вы делаете запрос, то по менему вы можете посмотреть, что произошло )
4. tracing
5. profiling (Pyroscope)



# System Design schema ![[Pasted image 20241019212625.png]]
Miro board:
	https://miro.com/app/board/uXjVLZJa5Mg=/