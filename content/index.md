---
seo:
  title: MikroORM 中文文档
  description: 基于 Data Mapper、Unit of Work 和 Identity Map 模式的 TypeScript ORM，支持 MongoDB、MySQL、PostgreSQL 等。
---

::u-page-hero{class="dark:bg-gradient-to-b from-neutral-900 to-neutral-950"}
---
orientation: horizontal
---
#top
:hero-background

#title
[MikroORM]{.text-primary}
TypeScript ORM

#description
基于 Data Mapper、Unit of Work 和 Identity Map 模式的 Node.js ORM。
支持 MongoDB、MySQL、MariaDB、PostgreSQL、SQLite 和 Better-SQLite。

#links
  :::u-button
  ---
  to: /quick-start
  size: xl
  trailing-icon: i-lucide-arrow-right
  ---
  快速开始
  :::
  :::u-button
  ---
  to: https://github.com/mikro-orm/mikro-orm
  target: _blank
  size: xl
  variant: subtle
  icon: i-simple-icons-github
  ---
  GitHub
  :::

#default
  :::prose-pre
  ---
  code: |
    @Entity()
    export class User {
      @PrimaryKey()
      id!: number;

      @Property()
      name!: string;

      @Property({ unique: true })
      email!: string;

      @OneToMany(() => Book, book => book.author)
      books = new Collection<Book>(this);

      constructor(name: string, email: string) {
        this.name = name;
        this.email = email;
      }
    }
  filename: user.entity.ts
  ---
  
  ```ts [user.entity.ts]
  @Entity()
  export class User {
    @PrimaryKey()
    id!: number;

    @Property()
    name!: string;

    @Property({ unique: true })
    email!: string;

    @OneToMany(() => Book, book => book.author)
    books = new Collection<Book>(this);

    constructor(name: string, email: string) {
      this.name = name;
      this.email = email;
    }
  }
  ```
  :::
::

::u-page-section{class="dark:bg-neutral-950"}
#title
核心特性

#features
  :::u-page-feature
  ---
  icon: i-lucide-database
  ---
  #title
  多数据库支持
  
  #description
  支持 MongoDB、MySQL、MariaDB、PostgreSQL、SQLite 等多种数据库，并在 API 层面保持统一。
  :::

  :::u-page-feature
  ---
  icon: i-lucide-shield-check
  ---
  #title
  类型安全
  
  #description
  完全使用 TypeScript 编写，提供一流的类型推断和智能提示体验，让开发更自信。
  :::

  :::u-page-feature
  ---
  icon: i-lucide-box
  ---
  #title
  Identity Map
  
  #description
  自动跟踪已加载的实体，确保在同一个上下文中多次获取同一记录时返回相同的对象实例。
  :::

  :::u-page-feature
  ---
  icon: i-lucide-layers
  ---
  #title
  Unit of Work
  
  #description
  自动处理事务，并在 flush 时将所有更改批量写入数据库，极大提高写入性能。
  :::

  :::u-page-feature
  ---
  icon: i-lucide-git-branch
  ---
  #title
  Schema 迁移
  
  #description
  内置强大的迁移工具，支持根据实体定义差异自动生成 SQL 迁移脚本，轻松管理数据库变更。
  :::

  :::u-page-feature
  ---
  icon: i-lucide-search
  ---
  #title
  Query Builder
  
  #description
  提供类型安全的 QueryBuilder，支持构建复杂的 SQL 查询（包括关联查询），同时保持代码的可维护性。
  :::
::

::u-page-section{class="dark:bg-gradient-to-b from-neutral-950 to-neutral-900"}
  :::u-page-c-t-a
  ---
  links:
    - label: 阅读文档
      to: '/quick-start'
      trailingIcon: i-lucide-arrow-right
    - label: 官方 GitHub
      to: 'https://github.com/mikro-orm/mikro-orm'
      target: _blank
      variant: subtle
      icon: i-simple-icons-github
  title: 准备好构建可扩展的应用了吗？
  description: 无论你是使用 SQL 还是 NoSQL，MikroORM 都能为你提供一致且强大的开发体验。
  class: dark:bg-neutral-950
  ---
  
  :stars-bg
  :::
::
