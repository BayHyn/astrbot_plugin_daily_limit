# 🚀 AstrBot 日调用限制插件 v2.0

<div align="center">

![Version](https://img.shields.io/badge/版本-v2.0-blue)
![AstrBot](https://img.shields.io/badge/AstrBot-3.5.1%2B-green)
![Python](https://img.shields.io/badge/Python-3.10%2B-yellow)
![License](https://img.shields.io/badge/License-MIT-orange)

**智能管理AI资源使用，防止滥用，提升用户体验**

[📖 文档](#文档) | [⚙️ 安装](#安装) | [🔧 配置](#配置) | [💡 使用](#使用) | [🔄 更新日志](#更新日志)

</div>

## ✨ 特性亮点

- 🛡️ **智能限制** - 基于每日调用次数的智能限制机制
- 👥 **多级权限** - 支持用户、群组、豁免用户三级权限管理
- 📊 **实时监控** - 提供使用统计、排行榜和状态监控
- 🔄 **灵活重置** - 支持单个用户或全部用户的使用次数重置
- 🎯 **精确控制** - 为不同用户和群组设置个性化限制
- 💾 **Redis支持** - 基于Redis的高性能数据存储

## 📖 文档

### 🎯 核心功能

本插件专为AstrBot设计，用于智能管理群组成员对大模型API的调用频率。通过精确的每日限制机制，有效防止资源滥用，确保AI服务的稳定性和公平性。

### 🔄 版本更新

**v2.0 主要更新：**
- ✅ 新增更多命令与功能
- ✅ 优化命令结构，使用更简洁直观
- ✅ 增强状态监控和统计功能
- ✅ 改进错误处理和用户体验

## ⚙️ 安装

### 系统要求

- **AstrBot版本**: v3.5.1+
- **Python版本**: 3.10+
- **Redis服务器**: 必须配置
- **依赖包**: `redis >= 4.5.0`

### 安装步骤

1. **安装Redis依赖**
   ```bash
   pip install redis>=4.5.0
   ```

2. **配置Redis服务器**
   - 确保Redis服务正常运行
   - 记录Redis连接信息（主机、端口、密码等）

3. **安装插件**
   - 将插件文件放置到AstrBot插件目录
   - 重启AstrBot服务

## 🔧 配置

### 📋 配置结构

插件配置文件采用JSON格式，包含以下主要部分：

#### Redis配置
```json
"redis": {
    "host": "localhost",
    "port": 6379,
    "db": 0,
    "password": ""
}
```

#### 限制配置
```json
"limits": {
    "default_daily_limit": 20,
    "exempt_users": [],
    "group_limits": [],
    "user_limits": []
}
```


### 📝 配置说明

#### 默认限制
- `default_daily_limit`: 所有用户的默认每日调用次数（默认：20次）

#### 豁免用户
- `exempt_users`: 不受限制的用户ID列表
- 优先级最高，豁免用户无调用次数限制

#### 群组限制
```json
{
    "group_id": "群组ID",
    "limit": 15
}
```

#### 用户限制
```json
{
    "user_id": "用户ID",
    "limit": 10
}
```

### 🔄 优先级规则

用户调用限制按以下优先级生效：
1. 🏆 **豁免用户** - 完全不受限制
2. 👤 **用户特定限制** - 针对单个用户的设置
3. 👥 **群组特定限制** - 针对整个群组的设置
4. ⚙️ **默认限制** - 全局默认设置

## 💡 使用

### 👤 用户命令

| 命令 | 功能 | 示例 |
|------|------|------|
| `/limit_status` | 查看个人使用情况 | `/limit_status` |
| `/限制帮助` | 显示所有可用命令 | `/限制帮助` |

### 👨‍💼 管理员命令

#### 🔧 基础管理
| 命令 | 功能 | 示例 |
|------|------|------|
| `/limit help` | 显示详细帮助 | `/limit help` |
| `/limit set <用户ID> <次数>` | 设置用户限制 | `/limit set 123456 50` |
| `/limit setgroup <次数>` | 设置群组限制 | `/limit setgroup 30` |

#### 🛡️ 豁免管理
| 命令 | 功能 | 示例 |
|------|------|------|
| `/limit exempt <用户ID>` | 添加豁免用户 | `/limit exempt 123456` |
| `/limit unexempt <用户ID>` | 移除豁免用户 | `/limit unexempt 123456` |

#### 📊 查询功能
| 命令 | 功能 | 示例 |
|------|------|------|
| `/limit list_user` | 列出用户限制 | `/limit list_user` |
| `/limit list_group` | 列出群组限制 | `/limit list_group` |
| `/limit top [数量]` | 显示排行榜 | `/limit top 5` |
| `/limit status` | 查看插件状态 | `/limit status` |

#### 🔄 重置功能
| 命令 | 功能 | 示例 |
|------|------|------|
| `/limit reset all` | 重置所有用户 | `/limit reset all` |
| `/limit reset <用户ID>` | 重置特定用户 | `/limit reset 123456` |

## 🔄 更新日志

### v2.0 (2025-01-23)
- 🚀 **性能提升**: 简化代码结构，提高执行效率
- 📊 **监控增强**: 改进状态检查和统计功能
- 💬 **交互优化**: 优化命令提示和错误处理

### v1.0.1 (2024-04-02)
- ✅ 初始版本发布
- ✅ 基础限制功能实现
- ✅ Redis数据存储支持
- ✅ 多级权限管理

## 📞 技术支持

### 🐛 问题反馈
如遇到任何问题，请通过以下方式联系：
- 📧 Telegram: [@TamakiSakura520](https://t.me/TamakiSakura520)
- 💬 Issues: [GitHub Issues](https://github.com/Sakura520222/astrbot_plugin_daily_limit/issues)

### 🤝 贡献指南
欢迎提交Pull Request来改进这个项目！

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

感谢原作者的贡献：
- 👨‍💻 **原作者**: left666
- 🔗 **原仓库**: [https://github.com/left666/astrbot_plugin_daily_limit](https://github.com/left666/astrbot_plugin_daily_limit)

---

<div align="center">

**🌟 如果这个插件对你有帮助，请给个Star支持一下！**

[![Star](https://img.shields.io/github/stars/Sakura520222/astrbot_plugin_daily_limit?style=social)](https://github.com/Sakura520222/astrbot_plugin_daily_limit)

</div>
