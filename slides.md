---
theme: seriph
background: /cover.png
layout: cover
download: 'https://antfu.me/talks/2021-04-29'
highlighter: shiki
info: |
  ## Go Way

  Design for Long Term Support applications

  [Boris Bobejko](https://t.me/anusdev) at Ostrovok Tech Talks

class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Go Way: Design for LTS Software
Как создать тестируемое ПО с длительным циклом эксплуатации и поддержки и не волноваться 

<div class="abs-br m-6 text-xl">
  <a href="https://t.me/anusdev" target="_blank" class="slidev-icon-btn">
      <logos:telegram />
  </a>
  <a href="https://github.com/godepo" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

---
layout: 'intro'
---

# Boris Bobejko

<div class="leading-8 opacity-80">
Software Engineer (2006 - *).<br>
Engineering Manager (2019-2023) <br>
Test-automation-freak - (2013 - *)<br>
Opensource Golang Depository Initiative - (2025-*)
</div>

<div class="my-10 grid grid-cols-[40px_1fr] w-min gap-y-4 items-center">

</div>

<img src="https://gravatar.com/userimage/156275414/c50a500ceb938f38c861db4298557af5.jpeg?size=256&cache=1740498954237" class="rounded-full w-40 abs-tr mt-16 mr-12"/>


---
transition: fade-out
---

# У го особый путь

- У нас не было времени, нам нужно было делать проект
- В первую очередь надо делать фичи
- Эти вещи сейчас не нужны, это оверинжиниринг.
- Никогда не знаешь, что будет в будущем.
- У нас микросервисы, каждый уникален.
- Если бы мы ещё и тесты писали, мы бы никогда никуда не успели.
- У нас уникальный проект и уникальные технические задачи

---
transition: slide-up
---

# Реальность

- Культура ответственность инженера, а не менеджера.
- Бизнес-задачи формализуются элементарно.
- Это профессии пахнут по разному, микросервисы - все одинаково.
- Архитектурные особенности в итоге выражаются одним и тем же способом.

---
transition: slide-up
layout: image-right
image: /punishment_sisyph.jpg

---

# Реальность
## Ручное тестирование

- годы на повторение регресса
- годы на проверку разработчиком
- месяцы на ожидание деплоя на стенды
- миллионы долларов из-за ошибок
- истощение от ручного скучного труда
- годы на воспроизведение дефектов

---
transition: slide-up
layout: image-left
image: /features.jpg
---

# Реальность
## Бизнес-фичи

- Важны только те, что принесут прибыль.
- И только те, что действительно работают.
- Не вызывают исков от клиентов. 
- Массово влияют только на KPI менеджера.
- И негативно на репутацию кодерка. 

---
transition: slide-down
layout: image-right
image: /engculture.jfif
---

# Реальность
## Инженерная культура

- Не интересует менеджеров
- Не компетенция управления
- Зависит от команды и инженеров
- Быть ответственным за свою работу
- Быть профессионалом

---
transition: slide-right
layout: section
---

# Секты и Религия

--- 
transition: fade
layout: image-right
image: /quartet.webp
---

# Религии

- Object Oriented Design
- Functional Programming
- Domain Driven Design
- Keep it simple, like u self

---
transition: slide-up
layout: image-right
image: /clean.png
---

# Секты 
## Object Oriented

- Mode-View-Controller - мало частей
- XXXXCVMNVBMNBC - мало смысла
- ООП - Объектно-ориентированное перепроектирование
- SOLID - DILDOS?
- Layers Architecture - у орков есть слои?
- Hexagonal Architecture - порты? адаптеры?

---
transition: fade
layout: image-right
image: /akka.png

---

# Секты 
## Functional Programming

- Effects - те что в инстаграмме?
- Actor Model - ни одной рабочей реализации в Open Source.
- IQ > 10 - не наш выбор
- Тем кому интересно - reference implementation: akka, vertx

---
transition: fade
layout: image-left
image: /ddd.jpg
---

# Domain Driven Design

- В каждой первой книге про него расскажут
- Во всех выглядит невнятно и безумно
- Два евангелиста не найдут общего языка
- Явно для Solution Architector'a
- Хочется их всех собрать вместе
- ... и заперев не кормить 
- ... чтобы понять кто же прав. 

---
transition: slide-up
layout: image-right
image: /simple-jack.webp
---

# Проблема GO: 
## для умственно отсталых.

- Примитивный синтаксис.
- Примитивный подход к решению проблем.
- Сделай сегодня, завтра оставь на завтра.
- Сделай и это и себя тупым.
 
---
transition: slide-up
layout: image-right
image: forrest.jpg
---

# Преимущества GO:
## Идеален для LTS

- Test suite
- Race conditions
- Stack full coroutines.
- Реактивная компиляция
- Asserts libraries
- Test Containers

---
transition: fade-in
layout: image-left
image: tsar.jfif
---

# Царь современного дизайна 
## Интерфейс

- Ориентирует на себя любой дизайн.
- Позволяет декларировать контракты.
- Позволяет инкапсулировать данные.
- Позволяет переопределять поведение.
- Предназначен для композиции.

---
transition: fade-out
---

# Определение ответственности компонентов

- Работа с хранилищами данных.
- Трансформация и обогащение данных.
- Транспорт данных.
- Кеширование данных.
- Верификация данных.

---
transition: fade-out
---


# Правила чистоплотности

- Принимаемые данные и реализация - разделены.
- Конструктор и внедрение зависимостей через него.
- Отсутствие публичных полей.
- Каждый связанный и используемый внутри компонент - это интерфейс описанный в модуле текущего компонента.
- Каждый метод - принимает context.Context.

---
transition: fade-out
---


# Пример компонента: TenantRepository

- Реализует способы хранения данных о тенанте, в базе данных postgresql.
- Позволяет проецировать реляционные отношения (таблицы) на структуры go.
- Позволяет использовать каждый определнный запрос и метод в общей транзакции с другими репозиториями.

---
transition: fade-out
---

# Создадим компонент и его контракт

- каталог repositories/tenant - для хранения DTO, доменной модели компонента и примитивов
- каталог repositories/tenant/pgtenant - для имплементации компонента, на основе postgresql

---
transition: fade-out
layout: two-cols
---


# Доменный тип: 

- Можем примитивно руками (go way)
- А можем и сгенерировать (smart way):
- а если сгенерированный код не устраивает, самое время написать свой перфоманс генератор.

::right::

# "Статус Тенанта"

```go
// ENUM(new, active, inactive, blocked, closed)
type State string

//go:generate go-enum --marshal --sql

```

---
transition: fade-out
layout: two-cols
---


# Доменный примитив 

- Это только кажется, что все UUID'ы и int64 отличная идея для идентификатора.
- А потом оказывается, что они генерируются где-то руками, где-то ногами.
- Или копируются непонятно откуда.
- Литерал же *tenant.ID* куда более говорит, о происходящем, чем *uuid.UUID*

::right::

# ID

```go
type ID uuid.UUID
```

---
transition: fade-in
layout: two-cols
---

# Доменная модель



- Аннотация "db" в тегах, говорит дженерик сканнеру pgx'a имя поля в результирующей выборке.
- LicensePlanID - ссылка на таблицу с планами лицензий.
- OwnerID - идентификатор фладельца тенанта.
- Name - название тенанта.

::right::

# Tenant

```go
type Tenant struct {
	ID            ID                `json:"id" db:"id"`
	Name          string            `json:"name" db:"name"`
	OwnerID       user.ID           `json:"owner_id" db:"owner_id"`
	LicensePlanID licenses.PlandID  `json:"license_plan_id" db:"license_plan_id"`
	State         State             `json:"state" db:"state"`
	CreatedAt     time.Time         `json:"created_at" db:"created_at"`
	UpdatedAt     time.Time         `json:"updated_at" db:"updated_at"`
	DeletedAt     *time.Time        `json:"deleted_at" db:"deleted_at"`
}

```

---
transition: fade-out
layout: two-cols-header
---
# Определим DTO  "создание Tenant'a"
::left::
- DTO (data transfer object) - нужен для отделения команд, от доменной модели
- Использование доменной модели, для команд и запросов (CQRS) приводит к загрязнению доменной модели
- А ей и так тяжело живётся.
::right::
```go
type CreateTenant struct {
	Name          string     `json:"name" db:"name"`
	OwnerID       user.ID    `json:"owner_id" db:"owner_id"`
	LicensePlanID license.ID `json:"license_plan_id" db:"license_plan_id"`
}
```
---
transition: fade-out
---

# Разберёмся с зависимостями

- *pgx.Pool
- UUID/v7

````md magic-move

```go
package pgtenants
```

```go
package pgtenants 

type DB interface {
}
```

```go
package pgtenants

type DB interface {
	Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
}
```

```go
package pgtenants 

type DB interface {
	Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
	Exec(ctx context.Context, query string, args ...interface{}) (pgconn.CommandTag, error)
}
```

```go
package pgtenants 

type DB interface {
	Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
	Exec(ctx context.Context, query string, args ...interface{}) (pgconn.CommandTag, error)
}

type IDGenerator func() (uuid.UUID, error)
```

```go
package pgtenants 

type DB interface {
	Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
	Exec(ctx context.Context, query string, args ...interface{}) (pgconn.CommandTag, error)
}

type IDGenerator func() (uuid.UUID, error)

type Repository struct {
	db          DB
	idGenerator IDGenerator
}
```

````
---
transition: fade-out
---

# Внедрим зависимости компонента

````md magic-move
```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}
```

```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)
```


```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)

func WithIDGenerator(idGenerator IDGenerator) Option {
	return func(r *Repository) {
		r.idGenerator = idGenerator
	}
}

```

```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)

func WithIDGenerator(idGenerator IDGenerator) Option {
	return func(r *Repository) {
		r.idGenerator = idGenerator
	}
}

func New(db DB, opts ...Option) *Repository {
```

```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)

func WithIDGenerator(idGenerator IDGenerator) Option {
	return func(r *Repository) {
		r.idGenerator = idGenerator
	}
}

func New(db DB, opts ...Option) *Repository {
	repo := &Repository{
		db:          db,
		idGenerator: uuid.NewUUID,
	}

```

```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)

func WithIDGenerator(idGenerator IDGenerator) Option {
	return func(r *Repository) {
		r.idGenerator = idGenerator
	}
}

func New(db DB, opts ...Option) *Repository {
	repo := &Repository{
		db:          db,
		idGenerator: uuid.NewUUID,
	}

    for _, opt := range opts {
		opt(repo)
	}
```


```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

type Option func(*Repository)

func WithIDGenerator(idGenerator IDGenerator) Option {
	return func(r *Repository) {
		r.idGenerator = idGenerator
	}
}

func New(db DB, opts ...Option) *Repository {
	repo := &Repository{
		db:          db,
		idGenerator: uuid.NewUUID,
	}

    for _, opt := range opts {
		opt(repo)
	}
	
	return repo
}
```

````

---
transition: fade-out
---

# "Create Tenant"
````md magic-move
```go
// добавим код метода для сохранения тенанта в postgresql
```

```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`
```
```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`

func (r *Repository) Create(ctx context.Context, obj tenant.CreateTenant) (empty tenant.ID, err error) {
```

```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`

func (r *Repository) Create(ctx context.Context, obj tenant.CreateTenant) (empty tenant.ID, err error) {
	id, err := r.idGenerator()
	if err != nil {
		return empty, fmt.Errorf("fail generate uuid for tenant id: %w", err)
	}
```

```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`

func (r *Repository) Create(ctx context.Context, obj tenant.CreateTenant) (empty tenant.ID, err error) {
	id, err := r.idGenerator()
	if err != nil {
		return empty, fmt.Errorf("fail generate uuid for tenant id: %w", err)
	}
	
	tag, err := r.db.Exec(ctx, createQuery, id, obj.Name, obj.LicensePlanID, obj.OwnerID)
	if err != nil {
		return empty, fmt.Errorf("fail create tenant: %w", err)
	}
```

```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`

func (r *Repository) Create(ctx context.Context, obj tenant.CreateTenant) (empty tenant.ID, err error) {
	id, err := r.idGenerator()
	if err != nil {
		return empty, fmt.Errorf("fail generate uuid for tenant id: %w", err)
	}
	
	tag, err := r.db.Exec(ctx, createQuery, id, obj.Name, obj.LicensePlanID, obj.OwnerID)
	if err != nil {
		return empty, fmt.Errorf("fail create tenant: %w", err)
	}

	if tag.RowsAffected() == 0 {
		return empty, fmt.Errorf("fail create tenant: affected  %d rows", tag.RowsAffected())
	}
```

```go
const createQuery = `
INSERT INTO lls.tenants
    (id, name, deleted_at, license_type_id, owner_id)
VALUES ($1, $2, $3, $4)
`

func (r *Repository) Create(ctx context.Context, obj tenant.CreateTenant) (empty tenant.ID, err error) {
	id, err := r.idGenerator()
	if err != nil {
		return empty, fmt.Errorf("fail generate uuid for tenant id: %w", err)
	}
	
	tag, err := r.db.Exec(ctx, createQuery, id, obj.Name, obj.LicensePlanID, obj.OwnerID)
	if err != nil {
		return empty, fmt.Errorf("fail create tenant: %w", err)
	}

	if tag.RowsAffected() == 0 {
		return empty, fmt.Errorf("fail create tenant: affected  %d rows", tag.RowsAffected())
	}
	return tenant.ID(id), nil
}
```
````

---
transition: fade-out
---

# Получение Tenant по ID

````md magic-move

```go
// Теперь реализуем функционал, для получения записи из базы, по её ID
```

```go
const getQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants 
WHERE id = $1
```

```go
const getQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants 
WHERE id = $1
`

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
```

```go
const getQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants 
WHERE id = $1
`

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go
const getQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants 
WHERE id = $1
`

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}

	obj, err := pgx.CollectOneRow(rows, pgx.RowToStructByName[tenant.Tenant])
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go
const getQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants 
WHERE id = $1
`

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}

	obj, err := pgx.CollectOneRow(rows, pgx.RowToStructByName[tenant.Tenant])
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
	return obj, nil
}
```
````
---
transition: fade-out
---

# Получим последние записи
````md magic-move
```go
// Напишем метод, который получит последние записи в определенном состоянии
```
```go
const findLastByStateWithLimitQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants
WHERE state = $1
ORDER BY created_at DESC
LIMIT $2
`
```
```go
const findLastByStateWithLimitQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants
WHERE state = $1
ORDER BY created_at DESC
LIMIT $2
`
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
```
```go
const findLastByStateWithLimitQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants
WHERE state = $1
ORDER BY created_at DESC
LIMIT $2
`
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
```
```go
const findLastByStateWithLimitQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants
WHERE state = $1
ORDER BY created_at DESC
LIMIT $2
`
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
	if err != nil {
		return nil, err
	}
```
```go
const findLastByStateWithLimitQuery = `
SELECT id, name, deleted_at, license_type_id, owner_id, created_at, updated_at, deleted_at
FROM lls.tenants
WHERE state = $1
ORDER BY created_at DESC
LIMIT $2
`
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
	if err != nil {
		return nil, err
	}
	return collectRows, nil
}
```
````

---
transition: fade
---

# Сервисный код?

````md magic-move
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, error){
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, error){
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, error){
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, error){
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
} 
```
````


---
transition: fade-out
layout: two-cols-header
---
# Результат

::left::
# Pros

- Абстрагировались от базы данных.
- Можно тестировать на моках, особенные случаи.
- Полностью совместимы с PGX.
- Шаблонный код для большинства сценариев
- Goland Live Templates
- Можно генерировать стандартные методы

::right::
# Cons

- Не используются транзакции
- Используем postgres словно это key/value
- Никакого ACID
- Нет изоляции транзакций

---
transition: fade
---

# Передадим транзакцию явно

````md magic-move
```go
func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go
type Querier interface {
    Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
}

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go

type Querier interface {
    Query(ctx context.Context, query string, args ...interface{}) (pgx.Rows, error)
}

func (r *Repository) FindByID(
    ctx context.Context,
    tx Querier, 
    id tenant.ID,
) (tenant.Tenant, error) {
    rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go
func (r *Repository) FindByID(
    ctx context.Context,
    tx Querier, 
    id tenant.ID,
) (tenant.Tenant, error) {
    if tx == nil {
        querier = r.db
    }
    
    rows, err := tx.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```

````

---
transition: fade
---

# Сервисный код?

````md magic-move
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tx, err := srv.db.Begin(ctx)
    if err != nil {
        return empty, fmt.Errorf("can't begin transaction: %w", err)
    }
    
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tx, err := srv.db.Begin(ctx)
    if err != nil {
        return empty, fmt.Errorf("can't begin transaction: %w", err)
    }
    
    tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tx, err := srv.db.Begin(ctx)
    if err != nil {
        return empty, fmt.Errorf("can't begin transaction: %w", err)
    }
    
    tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tx, err := srv.db.Begin(ctx)
    if err != nil {
        return empty, fmt.Errorf("can't begin transaction: %w", err)
    }
    
    tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Errorf("can't find tenants: %w", err)
    }
    
    if err = tx.Commit(); err != nil {
        return empty, fmt.Errorf("can't commit transaction: %w", err)
    }
    
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tx, err := srv.db.Begin(ctx)
    if err != nil {
        return empty, fmt.Errorf("can't begin transaction: %w", err)
    }

    defer func() {
        rollbackErr := tx.Rollback(ctx)
        if rollbackErr != nil && !errors.Is(rollbackErr, ErrTxClosed) {
            err = rollbackErr
		}
    }()
    
    tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Errorf("can't find tenants: %w", err)
    }
    
    if err = tx.Commit(); err != nil {
        return empty, fmt.Errorf("can't commit transaction: %w", err)
    }
    
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```

````


---
transition: fade
---
# Сервисный код?

````md magic-move
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
    if err != nil {
        return empty, fmt.Errorf("can't find tenant by id: %w", err) 
    }
    
    tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
    if err != nil {
        return empty, fmt.Error("can't find tenants: %w", err)
    }
    return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
}  
```

```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
        if err != nil {
            return empty, fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return empty, fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return empty, fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return empty, fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return empty, fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return empty, fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return empty, fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return empty, fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return empty, fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        return tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}, nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
````

---
transition: fade
layout: image-right
image: nevse.webp
---

# В чём проблема?

- Усложнение сигнатур
- Усложнение тестирования
- commit/rollback не для каждого
- Принесли в зависимость сервиса базу
- Без замыкания не обойтись
- Если правила поменяются?


---
transition: fade
---


# IDEA: Transactional Context
- Положить транзакцию в context
- Если в контексте нет транзакции - идём в db
- Всё так же, только без аргумента tx
- А сверху можно использовать Transaction Manager
- Минусы будут?

---
transition: fade
layout: image-right
image: strategy.png
---

# Минусы будут

- Go Way - разработчики не умеют в API.
- Использование никак не повлияет на код репозитория.
- [Avito Transaction Manager](https://github.com/avito-tech/go-transaction-manager).
- Avito - Russian Bigtech Company.
- Avito - лучший работодатель 2024 года.
- Avito - лидер платформизации.
- Посмотрим на платформизацию...

---
transition: fade
---

# Transactional Context/Manager
````md magic-move
```go
type Repository struct {
	db          DB
	idGenerator IDGenerator
}

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
    rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```

```go

import trmpgx "github.com/avito-tech/go-transaction-manager/drivers/pgxv5/v2"

type Repository struct {
	db          DB
	idGenerator IDGenerator
	txGetter *trmpgx.CtxGetter
}

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
    rows, err := r.db.Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
```go

import trmpgx "github.com/avito-tech/go-transaction-manager/drivers/pgxv5/v2"

type Repository struct {
	db          DB
	idGenerator IDGenerator
	txGetter *trmpgx.CtxGetter
}

func (r *Repository) FindByID(ctx context.Context, id tenant.ID) (tenant.Tenant, error) {
    rows, err := r.getter.DefaultTrOrDB(ctx, r.db).Query(ctx, getQuery, id)
	if err != nil {
		return tenant.Tenant{}, fmt.Errorf("fail get tenant: %w", err)
	}
```
````

---
transition: fade
---

# Эволюция сервисного кода

````md magic-move
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = pgx.BeginFunc(ctx, srv.db, func(tx pgx.Tx) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = srv.txManager.Do(ctx, func(ctx context.Context) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = srv.txManager.Do(ctx, func(ctx context.Context) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = srv.txManager.Do(ctx, func(ctx context.Context) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
````

---
transition: slide-up
layout: image-right
image: /tommygun.jpg
---

# Big Tech Platform

## Какая-то цыганщина

- Мы не решили проблему
- Репозиторий - тот же
- Кода стало больше
- Надо больше тестов
- Contextual Transaction - ничего не даёт?


---
transition: fade-out
layout: image-left
image: /thebrick.jpg
---

# Решение проблем

- Single Responsibility Principe
- Чем занимается Repository?
- Кто исполняет запрос?
- Кто должен определять где исполнять его?
- Видимо компонент DB, интерфейс которого мы определили.
- Нужно написать фасад.
- [Вообщ-то, он уже написан](https://github.com/godepo/elephant).
- Целых 6 звезд!

---
transition: fade-out
---

# Интерфейс царь, а можно ли больше?

- Мы уже смогли переложить ответственность на elephant-компонент для определения исполнения запроса.
- Можно использовать CQRS - исполнять пишущие транзакции на leader'e, а чтение на follower'e.
- Можно работать с шардированной базой.
- Можно собирать метрики для запросов, экспортируя их в prometheus без (почти) изменения кода.
- И всё это нам предоставил маленький интерфейс с всего-то двумя методами.

---
transition: fade-out
---

# Покажи мне код?

````md magic-move
```go
// языком чесать кто угодно может.
```
```go
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
```
```go
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
    ctx = elephant.With(ctx)
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
```

```go
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
    ctx = elephant.With(ctx, 
        elephant.WithMetricsLabel("tenants_repo", "find_last_by_state_with_limit"),
    )
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
```
```go
func (r *Repository) FindLastByStateWithLimit(
	ctx context.Context,
	state tenant.State,
	limit int,
) ([]tenant.Tenant, error) {
    ctx = elephant.With(ctx, 
        elephant.WithMetricsLabel("tenants_repo", "find_last_by_state_with_limit"),
        elephant.WithTimeout(time.Millisecond*100),
    )
	rows, err := r.db.Query(ctx, findLastByStateWithLimitQuery, state, limit)
	if err != nil {
		return nil, fmt.Errorf("fail get tenants: %w", err)
	}
	collectRows, err := pgx.CollectRows(rows, pgx.RowToStructByName[tenant.Tenant])
```
````

---
transition: fade-out
---


# Как выглядит управление транзакцией?
````md magic-move
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = srv.txManager.Do(ctx, func(ctx context.Context) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
```go
func (srv *Service) FindAllLastTenantsAndCurrent(
    ctx context.Context, 
    tenantID tenants.ID,
) (empty tenantsrv.ResponseAllLastTenantAndCurrent, err error){
    var result tenantsrv.ResponseAllLastTenantAndCurrent
    
    err = txManager.Transactional(ctx, func(ctx context.Context) error {
        tenant, err := srv.tenantsRepo.FindByID(ctx, tenantID)
        if err != nil {
            return fmt.Errorf("can't find tenant by id: %w", err) 
        }
        
        tenants, err := srv.tenantsRepo.FindLastByStateWithLimit(ctx, tenant.StateActive, tenant.DefaultRecordsLimit)
        if err != nil {
            return fmt.Error("can't find tenants: %w", err)
        }
        result = tenantsrv.ResponseAllLastTenantAndCurrent{Current: tenant, All: tenants}
        return nil
        })
    if err != nil {
        return empty, fmt.Errorf("something wrong in transaction: %w")
    }
    return result, nil
}  
```
````
---
transition: fade-out
---

# Transaction Manager?

```go
type TxManager interface {
	Transactional(
		ctx context.Context,
		fn func(ctx context.Context) error,
	) (out error)
}
```

- Запускает транзакцию и заворачивает её в контекст.
- Поддержка save points (nested tx).
- Автоматически делает rollback при ошибке.

---
transition: fade-out
---

# И это ещё не всё
````md magic-move
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	var result tenant.ID

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	result := tenant.NewID()

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	result := tenant.NewID()

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
		elephant.WithShardingKey(result.String())
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	result := tenant.NewID()

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
		elephant.WithShardingKey(result.String())
		elephant.WithTxOptions(pgx.TxOptions{IsoLevel: pgx.Serializable}),
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	result := tenant.NewID()

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
		elephant.WithShardingKey(result.String())
		elephant.WithIsolationSerializable,
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
```go
func (srv *Service) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (tenant.ID, error) {
	
	result := tenant.NewID()

	ctx = elephant.With(ctx, 
		elephant.WithCanWrite,
		elephant.WithShardingKey(result.String())
		elephant.WithIsolationSerializable,
		elephant.WithFnTxPassMatcher(func(ctx context.Context, err error) bool {
		    return errors.Is(err, tenant.ErrAlreadyExists)
		})
	)

	err := srv.txManager.Transactional(ctx, func(ctx context.Context) error {
```
````
---
transition: fade-out
---


# Что с эндпоинтами?

- Обработка ошибок.
- Верификация входных параметров.
- Проверка прав.

```go
func (hnd *Handlers) Create(
	ctx context.Context,
	req tenants.CreateRequest,
) (empty CreateResponse, err error) {
	if err = hnd.roles.HasAnyRole(ctx, user.RoleAdmin, user.RoleCanCreateTenants); err != nil {
		return empty, rest.ErrAccessDenied
	}
	id, err := hnd.tenants.Create(ctx, req)
	switch {
	case errors.Is(err, license.ErrNotFound) || errors.Is(err, user.ErrNotFound):
		return empty, fmt.Errorf("can not create tenant: %w: %w", rest.ErrBadRequest, err)
	case err != nil:
		return empty, fmt.Errorf("create tenants: %w: %w", rest.ErrInternalServerError, err)
	}
	return CreateResponse{ID: id}, nil
}
```

---
transition: fade
---
# Нужно немного поработать

````md magic-move
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)
```
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)

func Adapter[Req, Res any](fn func(context.Context, Req) (Res, error), interceptor ErrorInterceptor) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
```
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)

func Adapter[Req, Res any](fn func(context.Context, Req) (Res, error), interceptor ErrorInterceptor) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
		var req Req
		err := json.NewDecoder(r.Body).Decode(&req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusBadRequest)
			return
		}
```
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)

func Adapter[Req, Res any](fn func(context.Context, Req) (Res, error), interceptor ErrorInterceptor) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
		var req Req
		err := json.NewDecoder(r.Body).Decode(&req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusBadRequest)
			return
		}
		resp, err := fn(req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusInternalServerError)
			return
		}
```
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)

func Adapter[Req, Res any](fn func(context.Context, Req) (Res, error), interceptor ErrorInterceptor) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
		var req Req
		err := json.NewDecoder(r.Body).Decode(&req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusBadRequest)
			return
		}
		resp, err := fn(req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusInternalServerError)
			return
		}
		data, err := json.Marshal(resp)
		if err != nil {
			interceptor(r.Context(), w, fmt.Errorf("can't encode response: %w", err), http.StatusInternalServerError)
			return
		}
```
```go
type ErrorInterceptor func (ctx context.Context, w http.ResponseWriter, err error, code int)

func Adapter[Req, Res any](fn func(context.Context, Req) (Res, error), interceptor ErrorInterceptor) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
		var req Req
		err := json.NewDecoder(r.Body).Decode(&req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusBadRequest)
			return
		}
		resp, err := fn(req)
		if err != nil {
			interceptor(r.Context(), w, err, http.StatusInternalServerError)
			return
		}
		data, err := json.Marshal(resp)
		if err != nil {
			interceptor(r.Context(), w, fmt.Errorf("can't encode response: %w", err), http.StatusInternalServerError)
			return
		}
		w.Header().Set("Content-Type", "application/json")
		if err = w.Write(data); err != nil {
			logger.Error(r.Context(), "unexpected write error: %v", err)
		}
	}
}
```
````
---
transition: fade-out
---
# Перехватчик ошибок
````md magic-move
```go
type APIError struct {
	Code    int    `json:"-"`
	Status  int    `json:"status"`
	Message string `json:"message"`
}

```
```go
type APIError struct {
	Code    int    `json:"-"`
	Status  int    `json:"status"`
	Message string `json:"message"`
}

type APIResponse struct {
	Result any       `json:"result"`
	Error  *APIError `json:"error"`
}
```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
    if code == 0 {
        code = http.StatusInternalServerError
    } 

```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
    if code == 0 {
        code = http.StatusInternalServerError
    } 
    switch {
	case errors.As(err, &apiErr):
		response.Error = &apiErr
		code = apiErr.Code	
```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
    if code == 0 {
        code = http.StatusInternalServerError
    } 
    switch {
	case errors.As(err, &apiErr):
		response.Error = &apiErr
		code = apiErr.Code
	default:
		response.Error = &APIError{
			Message: err.Error(),
			Status:  http.StatusInternalServerError,
		}
	}
```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
    if code == 0 {
        code = http.StatusInternalServerError
    } 
    switch {
	case errors.As(err, &apiErr):
		response.Error = &apiErr
		code = apiErr.Code
	default:
		response.Error = &APIError{
			Message: err.Error(),
			Status:  http.StatusInternalServerError,
		}
	}
	data, err := json.Marshal(response)
	if err != nil {
		logger.Error(ctx, "fail serialize error: %v", err)
		w.WriteHeader(http.StatusInternalServerError)
		return
	}	
```
```go
func DefaultErrorInterceptor(ctx context.Context, w http.ResponseWriter, err error, code int) {
    if code == 0 {
        code = http.StatusInternalServerError
    } 
    switch {
	case errors.As(err, &apiErr):
		response.Error = &apiErr
		code = apiErr.Code
	default:
		response.Error = &APIError{
			Message: err.Error(),
			Status:  http.StatusInternalServerError,
		}
	}
	data, err := json.Marshal(response)
	if err != nil {
		logger.Error(ctx, "fail serialize error: %v", err)
		w.WriteHeader(http.StatusInternalServerError)
		return
	}
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(code)
	if _, err = w.Write(data); err != nil {
		logger.Error(ctx, "fail write error: %v", err)
		return
	}	
```
````
---
transition: fade-out
---
# Зачем всё это?

```go
func (hnd *Handlers) Router(mux *http.ServeMux) {
	mux.HandleFunc("/tenants/",
		Adapter[CreateRequest, CreateResponse](
			hnd.Create,
			DefaultErrorInterceptor,
		),
	)
}
```

---
transition: fade-out
---
# Что с обработкой очередей?

- Тут сложнее, классически нормальная обработка у очередей практически не существует.
- Можно как-то жить с паттерном Outbox.
- Сложность с согласованием коммитов в очередь и постгрес, нужно уметь в индепотентность.
- Можно использовать CDC (debezium) или написать самим через LOCK FOR UPDATE.
- Ну или в некоторых случаях научится пользоваться логической репликацией постгреса (ещё одна фича в elephant).
- Но рецепт тот же - интерфейсы.

---
transition: fade-out
---

# Каким должно быть классическое го-приложение?

- 1 бинарник и одна входная main точка.
- Если есть CLI должно запускаться с того же main.
- Нужно уметь в graceful shutdown.
- Нужно уметь запустить всё приложение со всеми зависимостями без захода в main.
- Но как?

---
transition: fade-out
---


# Application container.

- Нужен для связывания всех зависимостей
- Нужен для переопределения зависимостей для интеграционных тестов.
- Нужен для запуска и остановки приложения.
- Есть google/wire (генерация, статика)
- Есть uber/fx (рефлексия, динамика)
- Для CLI можно использовать динамический контейнер, чтобы для каждой команды подгруждать только ее зависимости.

---
transition: fade-out
---

# Uber Sample

```go
func App() fx.Option {
	fx.Options(
		fx.Provide(
			appcfg.New,
			pgdb.Provide,
			pgtenant.New,
			pguser.New,
			pglicense.New,
			tenants.New,
			rest.New,
		),
		fx.Invoke(
			preloadCache,
			printGraph,
			registerRunners,
		),
	)
}
func New() {
	fx.New(App()).Run()
}

```

---
transition: fade-out
---


# А как же выглядит такой main?

```go
var createApp = app.New

func main() {
	createApp()
}
```

- Просто берём функцию конструктора и гоним её вперёд!
- Давайте угадаем, зачем мы именно так используем функцию app.New?

---
transition: fade-out
---

# Что нам дал Application Container?

- Можно проверить написав тест, что все зависимости работают.
- Можно кое-что переопределить в функции App, с паттерном функциональных опций.
- Можно замокать сети, можно запустить в контейнерах постгресы и очереди.
- И прогнать сквозные бизнес-сценарии.
- Можно заместить очереди (они же скрыты за интерфейсами) каналами и проверить всё даже без очередей.
- Можно заместить сеть каналами и протестить работу сервисов без какой-либо сети (отлично работает с grpc).
- Неважно какое у вас приложение - обычный http-микросервис, ETL или игровой сервис на акторной модели - вы сможете его запустить и протестировать.

---
transition: fade-out
---

# В чём сложности.

- Много мелких зависимостей и компонентов.
- Аккуратно нужно разбираться в этом графе зависимостей и связывать компоненты.
- Много файлов, много навигации, много импортов.
- Много мелких файлов, большая и ветвистая иерархия директорий.
- Мало хороших инструментов (таких как слоняра).
- Интерфейсы могут быть медленными. Впрочем, вся сеть в стандартной библиотеке го написана то именно на них.
- Надо работать, над дизайном приложения.
- Ещё и тесты придётся писать, ведь до всего можно добраться.

---
transition: fade-out
---


# В чем плюсы.

- Нет ничего, что не получится протестировать разработчику.
- Ограничение только в фантазии и времени.
- При наличии связанного конечного тестирования, 1 успешный тест на фичу и 100% покрытие unit-test'ов, на 142% процента гарантирует работспособность функционала.
- Быстрые итерации, го быстро компилируется, быстро запускает тесты. Можно подготовить фичу задолго до регресса и смоука от QA.
- В отпуск можно идти когда угодно, даже всем вместе на новый год.
- Даже если нужны дежурные, хороший код не имеет привычек ломаться.
- Нет страха перед изменением.

---
transition: fade-out
---

# В чём проблема.

- А больше не нужна большая команда QA.
- И больше не нужна большая команда разработки, т.к. 1-2 человека могут справляться с огромным потоком задач, даже в MSA.
- Больше нет Job Security.
- При отсутствии инструментов - их придётся делать, ведь коммьюнити идёт по дорожке go-way.
