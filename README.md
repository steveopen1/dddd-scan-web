![image](https://github.com/user-attachments/assets/a5376af2-150e-4ed5-839f-6228cf029a70)# dddd-scan-web
本工具是一个基于 Flask 框架构建的任务管理与报告生成系统。它允许用户提交任务（如 dddd.exe 工具执行的扫描任务），并对任务进行管理，包括查看任务状态、终止任务、删除任务等操作。同时，系统支持任务日志的查看和导出，能够将任务结果以 HTML 和 JSON 格式保存，并提供了将 JSON 日志导出为 Excel 文件的功能。此外，系统集成了认证模块，确保只有经过授权的用户才能访问相关功能。
以下是根据你提供的代码生成的 README 文档和简介(作为学习flask的项目)：

### 简介
本工具是一个基于 Flask 框架构建的任务管理与报告生成系统。它允许用户提交任务（如 `dddd.exe` 工具执行的扫描任务），并对任务进行管理，包括查看任务状态、终止任务、删除任务等操作。同时，系统支持任务日志的查看和导出，能够将任务结果以 HTML 和 JSON 格式保存，并提供了将 JSON 日志导出为 Excel 文件的功能。此外，系统集成了认证模块，确保只有经过授权的用户才能访问相关功能。
![image](https://github.com/user-attachments/assets/4bd78788-910b-4a9f-81de-323c97afb7b7)
![image](https://github.com/user-attachments/assets/9d47bdda-5c07-48d5-a2ee-82d3dafc0dd6)
![image](https://github.com/user-attachments/assets/de2c08b8-3b1a-4855-a994-1d17b6101115)
![image](https://github.com/user-attachments/assets/7dac77f7-afdc-49c8-a513-73e01db855a3)
![image](https://github.com/user-attachments/assets/45ea9366-6084-44c3-9da4-af66fac729b6)



### README 文档

# 任务管理与报告生成系统

## 概述
本系统是一个基于 Flask 的 Web 应用程序，用于管理任务和生成报告。它允许用户提交任务、查看任务状态、终止任务、删除任务以及导出任务日志。系统使用 SQLite 数据库来存储任务信息，并支持将任务结果以 HTML 和 JSON 格式保存。

## 功能特性
- **任务管理**：用户可以提交任务到队列，并查看任务的状态（待处理、运行中、已完成、失败、已停止）。
- **任务终止**：用户可以终止正在运行的任务。
- **任务删除**：用户可以删除已完成、失败或已停止的任务。
- **报告生成**：系统会生成任务的 HTML 和 JSON 报告，并存储在 `result` 目录下。
- **日志导出**：用户可以导出所有任务的日志或单个任务的日志为 Excel 文件。
- **认证机制**：系统集成了认证模块，确保只有经过授权的用户才能访问相关功能。

## 安装与配置

### 环境要求
- Python 3.x
- Flask
- Flask-SQLAlchemy
- Flask-CORS
- psutil
- pandas
- openpyxl

### 安装依赖
```bash
pip install flask flask-sqlalchemy flask-cors psutil pandas openpyxl
```

### 配置
1. 确保 `dddd.exe` 工具在系统的可执行路径中，或者在代码中指定正确的路径。
2. 配置数据库连接，默认使用 SQLite 数据库，数据库文件名为 `tasks.db`。

### 运行应用
```bash
python main.py
```

## 使用说明

### 访问应用
启动应用后，打开浏览器并访问 `http://127.0.0.1:5000`。

### 提交任务
- 访问 `/run_spray` 接口，通过 POST 请求提交任务。可以提交 IP 地址或上传包含 IP 地址的文件。
- 支持的参数包括 `ip`、`port`、`saveToFile`、`projectName` 和 `infoCollectionOnly`。

### 查看任务状态
- 访问 `/api/tasks` 接口，通过 GET 请求获取所有任务的信息。

### 终止任务
- 访问 `/api/tasks/<int:task_id>/stop` 接口，通过 POST 请求终止指定 ID 的任务。

### 删除任务
- 访问 `/api/tasks/<int:task_id>` 接口，通过 DELETE 请求删除指定 ID 的任务。

### 查看报告
- 访问 `/reports` 页面，查看所有任务的报告列表。
- 访问 `/report/<path:filename>` 接口，查看指定报告文件。

### 导出日志
- 访问 `/export_logs` 接口，通过 GET 请求导出所有任务的日志为 Excel 文件。
- 访问 `/export_single_log/<path:filename>` 接口，通过 GET 请求导出指定任务的日志为 Excel 文件。

## 目录结构
```
.
├── auth/              # 认证模块
├── database.py        # 数据库配置
├── main.py            # 主应用程序
├── reports_blueprint.py # 任务和报告相关的蓝图
├── result/            # 任务结果存储目录
├── temp/              # 临时文件存储目录
└── templates/         # HTML 模板文件
```

## 注意事项
- 确保 `dddd.exe` 工具可以正常运行，并且具有执行所需任务的权限。
- 确保临时目录和结果目录具有读写权限。
- 系统使用的初始密码会在应用启动时生成并记录在日志中。

## 贡献
如果你有任何改进建议或发现了 bug，请在 GitHub 上提交 issue 或 pull request。

## 许可证
本项目采用 [MIT 许可证](LICENSE)。
