# spring-security-dome
基于Spring-Security的安全访问控制设计与实现


3.3.数据库设计

项目根目录下新建文件create.sql .创建用户表user .角色表role.用户角色表user_ role，系统至少需要创建两个用户.分别指定不同的角色user,admin.

3.4.用户密码安全

用户密码采用Pbkdf2PasswordEncoder加密.并且指定密钥secret=aheader

3.5.控制层URI指相对URL.表示去掉http://localhost:8080/后的内容)

A登录页面URI=my/login，登录失败跳转到页面URI=my/error .任何用户登录

成功跳转页面URI=user/home ;

B只有user角色才能访问页面URI=user/self;

C只有admin角色才能访问的页面URI-admin/self;

D.在URI=user/home页面点击<退出>链接URI=logout.即退出系统. 跳转到登录

页面URI=my/login; .

E.通过URI=myrencode/{password).使用3.4定义的加密规则，对传人的密码参

数加密.然后输出加密后的结果;

3.6.数据层

通过mybatis访问mysq|数据库. SQL语句 写在映射文件里面.

3.7.服务层

用户接OUserService .角色接ORoleService

3.8.安全配置和自定义认证

安全配置类MySecurityConfiguration

自定义认证UserDetailsService接口实现类MyUserDetailsServicelmpl
