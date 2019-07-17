## 打怪升级任务
1. 执行 `ansible-playbook -i hosts playbook.yml` 成功
2. 创建用户 apps 及用户组 apps：
    * user 模块: https://docs.ansible.com/ansible/latest/modules/user_module.html
    * group 模块: https://docs.ansible.com/ansible/latest/modules/group_module.html
3. 创建以下文件夹，并设置文件夹的用户和组为 apps：
    /apps，/apps/hello，/apps/hello/bin，/apps/hello/logs
    * file 模块: https://docs.ansible.com/ansible/latest/modules/file_module.html
4. 将 helloworld-0.0.2.jar copy 到 /apps/hello/bin 目录下，设置该 jar 文件的用户和用户组为 apps
    * copy 模块: https://docs.ansible.com/ansible/latest/modules/copy_module.html
5. 使用 template 模块将 app.service copy 到目标服务器的 /etc/systemd/system 中，并重命名 hello.service :
    * template 模块: https://docs.ansible.com/ansible/latest/modules/template_module.html
6. 启动 hello 服务
    * service 模块: https://docs.ansible.com/ansible/latest/modules/service_module.html
7. 监听 hello 服务是否启动成功
    * wait_for 模块: https://docs.ansible.com/ansible/latest/modules/wait_for_module.html
8. 为目标机器安装 JDK 1.8:
    1. 在本地仓库中创建 roles 目录
    2. clone 代码：https://github.com/geerlingguy/ansible-role-java 到 roles 目录中
    3. 在 playbook.yml 文件中加入 ansible-role-java 的role
9. 创建自定义 role: hello role
    1. 进入 roles 目录：cd roles
    2. 使用命令生成 role 模板：`ansible-galaxy init hello`
    3. 将 hello 的部署逻辑（在 playbook.yml 中）写入到 hello role 中
10. 将 hello 部署到多台机器
    * 需要修改 hosts 文件
11. 多环境部署