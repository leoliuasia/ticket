
# 快速部署

1.clone项目到本地```https://github.com/stevlu/ticket.git```

2.数据库脚本放在ticketserver项目的resources目录下，在Oracle中执行数据库脚本OracleSetup.sql，包括建表、sequence、trigger、procedure，及插入测试内容

3.数据库配置在ticketserver项目的resources目录下的application.properties文件中  

4.在IntelliJ IDEA中运行ticketserver项目  

**OK，至此，服务端就启动成功了，此时我们直接在地址栏输入```http://localhost:8082/index.html```即可访问我们的项目，如果要做二次开发，请继续看第五、六步。**  

5.进入到ticketui目录中，在命令行依次输入如下命令：  

```
# 安装依赖
npm install

# 在 localhost:80 启动项目
npm run dev
```  

由于我在ticketui项目中已经配置了端口转发，将数据转发到SpringBoot上，因此项目启动之后，在浏览器中输入```http://localhost:80```就可以访问我们的前端项目了，所有的请求通过端口转发将数据传到SpringBoot中（注意此时不要关闭SpringBoot项目）。  

6.最后可以用WebStorm等工具打开ticketui项目，继续开发，开发完成后，当项目要上线时，依然进入到ticketui目录，然后执行如下命令：  

```
npm run build
```  

该命令执行成功之后，ticketui目录下生成一个dist文件夹，将该文件夹中的两个文件static和index.html拷贝到SpringBoot项目中resources/static/目录下，然后就可以像第4步那样直接访问了。  


**步骤5中需要大家对NodeJS、NPM等有一定的使用经验，不熟悉的小伙伴可以先自行搜索学习下，推荐[Vue官方教程](https://cn.vuejs.org/v2/guide/)。**  
