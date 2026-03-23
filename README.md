# 我的百科

一个极简的个人词条网站，用于记录我对万物的理解与联想。

## 项目结构

```
/
├── index.html     # 主页面（全部逻辑在此）
├── entries.js     # 所有词条数据
└── README.md
```

**仓库体积极小**，无任何框架依赖，无 node_modules。字体通过 Google Fonts CDN 加载。

---

## 部署到 GitHub Pages

1. 在 GitHub 创建一个新仓库（名称随意，如 `baike`）
2. 将这两个文件上传：`index.html`、`entries.js`
3. 进入仓库 **Settings → Pages**
4. Source 选择 **Deploy from a branch**，Branch 选 `main`，目录选 `/ (root)`
5. 保存，等待约 1 分钟，即可通过 `https://你的用户名.github.io/baike/` 访问

---

## 绑定自定义域名

1. 在仓库根目录添加一个名为 `CNAME` 的文件（无扩展名），内容为你的域名，例如：
   ```
   baike.yourdomain.com
   ```
2. 在你的域名 DNS 管理处添加 CNAME 记录：
   - 主机名：`baike`（或你想用的子域名）
   - 指向：`你的用户名.github.io`
3. 回到 GitHub Pages 设置，填入自定义域名，勾选 **Enforce HTTPS**

---

## 添加词条

编辑 `entries.js`，在 `ENTRIES` 数组里添加新对象：

```js
{
  id: "词条id",          // 英文/拼音，用作 URL，不能有空格
  title: "词条标题",      // 中文词语
  pinyin: "pīn yīn",    // 拼音（用于排序和显示）
  content: `正文内容，支持：
## 二级标题
**加粗文字**
[[其他词条]]  ← 自动变成内部链接 `,
  related: ["其他词条id", "另一个词条id"]  // 相关词条（可选）
}
```

---

## 正文格式说明

| 语法 | 效果 |
|------|------|
| `## 标题` | 二级标题 |
| `**文字**` | 加粗 |
| `[[词语]]` | 跳转到该词条的内链 |
| 空行分隔 | 新段落 |
