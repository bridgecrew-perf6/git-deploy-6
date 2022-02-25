# git-deploy

结合git完成一键自动化部署项目，摆脱手动打包和拷贝文件的操作。


初始化配置只会生成 `dev` (开发环境)、`test` (测试环境)、`prod` (生产环境) 三个配置，再有其他配置可参考模板自行配置。
在项目根目录下手动创建 `git-deploy.config.js` 文件，复制以下代码按情况修改即可。

```javascript
module.exports = {
  projectName: 'vue_samples', // 项目名称
  privateKey: '/Users/uchengwei/.ssh/id_rsa',
  passphrase: '',
  dev: {
    // 环境对象
    name: '开发环境', // 环境名称
    script: 'npm run serve', // 打包命令
    host: '192.168.1.1', // 服务器地址
    port: 22, // 服务器端口号
    username: 'root', // 服务器登录用户名
    password: '123456', // 服务器登录密码
    distPath: 'dist', // 本地打包生成目录
    webDir: '/usr/local/html', // 服务器部署路径（不可为空或'/'）
    bakDir: '/usr/local/fs', // 备份路径
    isRemoveRemoteFile: true, // 是否删除远程文件（默认true）
    isRemoveLocalFile: true // 是否删除本地文件（默认true）
    isCommit: false, // 是否提交更新本地代码
    targetBranch: '', // 要发布的分支
    isDeploy: true, // 是否发布
  }
  
}
```

