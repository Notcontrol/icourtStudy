### 完成条件：
1. 能正常启动自己的项目，并能访问自己的controller
2. 了解spring boot的基本知识
3. 提交到github中
4. 附加项。spring boot mybatis 工程demo 搭建 包括swagger 增删改查业务

# 创建项目
1. 使用idea创建springBoot项目注意勾选web组件依赖。
2. 创建完成项目之后新建一个controller包，在包中新建一个DemoController。
## DemoController
```
 @Slf4j
 @Api(value = "demo api")
 @RestController
 @RequestMapping("/api/v1/")
 public class DemoController {
 
 
     @Resource
     IUserService iUserService;
 
     /**
      * 获取信息
      * @param userId 用户的id
      * @return 用户信息
      */
     @ApiOperation(value = "获取用户详细信息", notes = "根据用户的url中的id来获取他的详细信息")
     @ApiImplicitParam(name = "userId", value = "用户id", required = true, dataType = "Integer", paramType="path")
     @GetMapping("users/{userId}")
     public ResponseEntity<User> getUsersById(@PathVariable(value = "userId") Integer userId){
         User user = iUserService.getUser(userId);
         log.debug("log test");
         return ResponseEntity.ok(user);
     }
 
 } 
 ```
### 几个注解的作用
 * @RestController 这个注解是@Controller和@ResponseBody的组合用来向客户端返回json格式数据
 * @GetMapping 这个注解用来接收get请求
 * @Api 修饰整个类，描述controller的作用
 * @ApiOperation 描述一个类的其中一个方法的作用
 * @ApiImplicitParam 一个请求参数是使用这种方式
 * @Slf4j 使用此注解需要先在项目中添加lombok依赖，并装上lombok插件。
 使用此注解之后不必再使用LoggerFactory创建log。在项目可以直接使用log
 
 ### 经柴导师指出的一些不规范或出错的地方
 * 未按照开发文档中的规定 URI必须返回版本信息;
 * 项目中使用ResponseEntity中的泛型可以直接将结果返回，不用再进行二次封装;
 * 项目中mybatis的Dao中统一使用xml的形式，不使用注解形式;
 * 未起作用的import要删除;

## Swagger学习
1. Swagger是什么：
    能够自动生成api文档的框架，并对api进行一些测试。
2. Swagger怎么用:
    pom中添加swagger依赖，创建swagger配置类，并开启。 
3. swagger配置类
    
## SwaggerConfig 
 ```$xslt
/**
 * swagger配置类
 *
 * @author jianglu
 * Created 2018 - 07 - 28 - TIME
 */
@Configuration
@EnableSwagger2
public class SwaggerConfig {

    @Bean
    public Docket createRestApi() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.example.swaggerdemo.controller"))
                .paths(PathSelectors.any())
                .build();
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("利用swagger构建api文档")
                .description("这里是一个描述信息。这个仅仅是一个小demo")
                .termsOfServiceUrl("http://icourt.cc")
                .version("1.0")
                .build();
    }

}
```
### 其中的注解作用
 * @Configuration 将该类作为配置类，相当于在使用xml形式时在xml文件中配置的beans
 * @EnableSwagger2 启动swagger
 * @Bean 等同于在xml中配置的bean
### 注意事项
 * basePackage中是项目api接口包路径

4. 访问:http://localhost:8080/swagger-ui.html 查看生成的api文档。
# Spring Boot入门
1. 自动配置，应用程序中的常见功能，能够自动配置
2. 起步依赖，将常用的库聚合在一起，例如只需要依赖一个spring-boot-starter-web就可以将常用的依赖加到项目里面


## 项目已上传至github 
地址:https://github.com/Notcontrol/swagger-demo.git