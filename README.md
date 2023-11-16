# AutoGreen

每日自动commit，保持 Github 提交状态全绿。

## 原理

使用 Github Actions 的定时任务功能，每隔一段时间自动执行 `git commit`，提交信息为 "Github Daily Auto Commit!"。

## 使用

- 创建 Github 仓库，点击Actions，再点击Configure
- 复制 .github/workflows 下的 auto_green.yml 文件
- 将 auto_green.yml 文件第19和20行修改为自己的信息
- 修改 auto_green.yml 文件第8行来调整每日提交的频率(可选)

## 解释

计划任务语法有 5 个字段，中间用空格分隔，每个字段代表一个时间单位。

```plain
┌───────────── 分钟 (0 - 59)
│ ┌───────────── 小时 (0 - 23)
│ │ ┌───────────── 日 (1 - 31)
│ │ │ ┌───────────── 月 (1 - 12 或 JAN - DEC)
│ │ │ │ ┌───────────── 星期 (0 - 6 或 SUN - SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

每个时间字段的含义:

| 符号 | 描述     | 举例                                    |
| ---- | -------- | --------------------------------------- |
| `*`  | 任意值   | `* * * * *` 每天每小时每分钟            |
| `,`  | 值分隔符 | `1,3,4,7 * * * *` 每小时的 1 3 4 7 分钟 |
| `-`  | 范围     | `1-6 * * * *` 每小时的 1-6 分钟         |
| `/`  | 每       | `*/15 * * * *` 每隔 15 分钟             |

**注:** 由于 Github Actions 的限制，如果设置为 `* * * * *` 实际的执行频率为每 5 分钟执行一次。

## License

[auto-green](https://github.com/justjavac/auto-green) is released under the MIT License. See the bundled [LICENSE](./LICENSE) file for details.

