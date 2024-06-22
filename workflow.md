# 计划分析：

1. **从 bubble list 开始**：
   - **理由**：bubble list 项目相对简单，适合快速上手。通过这个项目，你可以熟悉Gin和Gorm的基本用法，了解项目的整体架构和运行流程。
   - **学习目标**：
     - 熟悉Gin框架的基本路由和中间件功能。
     - 了解Gorm的基本CRUD操作。
     - 学习项目的基本配置和启动流程。

2. **然后学习 lite_blog**：
   - **理由**：lite_blog 项目更复杂，涉及到前后端整合、容器化部署等高级内容。在掌握了基础之后，继续深入学习更复杂的项目，有助于全面提升你的开发技能。
   - **学习目标**：
     - 深入理解MVC架构和控制器、模型、视图的交互。
     - 学习如何使用Docker进行项目的容器化部署。
     - 了解项目的前端和后端整合，掌握全栈开发技能。

# 工作日志 Bubble_List

## 2024年6月22日
### 引入GORM不会在电脑上面安装MySQL数据库
你的 Go 文件中引入了 MySQL 的 GORM 驱动，但这并不会自动在你的电脑上安装 MySQL 数据库。下面是解释：

1. **引入包的作用**：
   ```go
   import (
       "github.com/jinzhu/gorm"
       _ "github.com/jinzhu/gorm/dialects/mysql"
   )
   ```
   引入 `"github.com/jinzhu/gorm/dialects/mysql"` 只是为了让 GORM 知道如何与 MySQL 数据库进行交互，但它并不会安装 MySQL 数据库。你需要确保 MySQL 数据库已经在你的系统上安装并正在运行。

2. **连接到 MySQL 数据库**：
   ```go
   dsn := fmt.Sprintf("%s:%s@tcp(%s:%d)/%s?charset=utf8mb4&parseTime=True&loc=Local",
       cfg.User, cfg.Password, cfg.Host, cfg.Port, cfg.DB)
   DB, err = gorm.Open("mysql", dsn)
   ```
   这段代码用于生成连接字符串并使用 GORM 连接到 MySQL 数据库。但是，如果你的系统上没有安装 MySQL 数据库，这段代码会失败，因为它找不到可以连接的 MySQL 服务。

3. **需要安装 MySQL 数据库**：
   如果你没有安装 MySQL 数据库，你可以通过以下几种方式来安装：
   - **手动安装**：可以通过 MySQL 的官方网站下载并安装适合你操作系统的版本。
   - **使用 Docker**：如果你熟悉 Docker，可以使用 Docker 来快速启动一个 MySQL 实例。例如：
     ```sh
     docker run --name mysql -e MYSQL_ROOT_PASSWORD=root -d mysql:latest
     ```
     然后，你可以将 `cfg.Host` 设置为 `localhost` 或者 Docker 容器的 IP 地址，`cfg.Port` 设置为 3306（默认的 MySQL 端口）。

4. **验证安装**：
   安装 MySQL 数据库后，你可以通过命令行工具或 GUI 客户端（如 MySQL Workbench）来验证 MySQL 数据库是否正在运行，并确保你能够连接到它。

总之，你的 Go 代码不会自动下载或安装 MySQL 数据库。你需要确保你的开发环境中已经安装并运行了 MySQL 数据库，然后你的代码才能正常连接并使用 MySQL。


---

## 2024年6月23日

### 今日任务
- 配置了 Gin 项目结构，分离了控制器和路由文件

---