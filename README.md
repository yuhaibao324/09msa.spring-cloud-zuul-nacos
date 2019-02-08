# spring-cloud-zuul-nacos
zuul集成Nacos实现动态路由

# 0.Spring Cloud Zuul动态路由实现思路
    源码：https://github.com/SpringCloud/spring-cloud-zuul-nacos
   
# 1.启动nacos (下载nacos-server-0.8.0)
    启动脚本： D:\devtools\nacos\nacos-server-0.8.0\nacos\bin\startup.cmd
   
# 2. 点击配置列表--》单击右侧的+号图标--》新增一项配置：

    DataId:zuul-server
    Group:zuul_route
    配置内容
    [
           {
               "enabled":true,
               "id":"erer",
               "path":"/baidu/**",
               "retryable":false,
               "stripPrefix":true,
               "url":"http://github.com/Lovnx"
           },
           
           {
               "enabled":true,
               "id":"pppp",
               "path":"/client/**",
               "retryable":false,
               "stripPrefix":true,
               "url":"http://localhost:7070"
           }
       ]
   
# 3. 启动zuul-server，从Nacos加载路由信息测试


# 4. 测试
    4.1 访问：  http://localhost:5555/baidu
    
    4.2 修改nacos的zuul配置信息
    [
        {
            "enabled":true,
            "id":"erer",
            "path":"/baidu/**",
            "retryable":false,
            "stripPrefix":true,
            "url":"http://www.baidu.com"
        },
        
        {
            "enabled":true,
            "id":"pppp",
            "path":"/client/**",
            "retryable":false,
            "stripPrefix":true,
            "url":"http://localhost:7070"
        }
    ]
    
    4.3 访问： http://localhost:5555/baidu