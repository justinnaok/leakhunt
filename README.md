# leakhunt

**检测评测集与训练语料的重复片段。**

`leakhunt` —— 对评测样本做近重复匹配，标出与已知语料高度重合的样本

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`leakhunt.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install justinnaok-leakhunt
```

装完直接用命令名调用：

```bash
leakhunt --help
```

也可以不用安装，直接把 `leakhunt.py` 拷走用——它只依赖标准库。

## 为什么需要它

用 n-gram 指纹做近重复判定，不要求完全一致

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 评测数据泄漏 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python leakhunt.py --file input.txt
python leakhunt.py --text "示例内容"
python leakhunt.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 近重复用字符 shingle 估算，长文本阈值需自己调。
- 只报告重复项，不删数据。

## 跑测试

```bash
python test_leakhunt.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/justinnaok/leakhunt>

---

## 关于作者

justinnaok 做评测数据泄漏相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://justinnaok.github.io>
- 仓库：<https://github.com/justinnaok/leakhunt>

## 许可

MIT，见 [LICENSE](LICENSE)。
