<p align="center">
  <a href="https://github.com/baomidou/mybatis-plus">
   <img alt="Mybatis-Plus-Logo" src="https://raw.githubusercontent.com/baomidou/logo/master/mybatis-plus-logo-new-mini.png">
  </a>
</p>

<p align="center">
  Born To Simplify Development
</p>

<p align="center">
  <a href="https://search.maven.org/#search%7Cga%7C1%7Cg%3A%22com.baomidou%22%20AND%20a%3A%22mybatis-plus%22">
    <img alt="maven" src="https://img.shields.io/maven-central/v/com.baomidou/mybatis-plus.svg?style=flat-square">
  </a>

  <a href="https://github.com/996icu/996.ICU/blob/master/LICENSE">
    <img alt="996icu" src="https://img.shields.io/badge/license-NPL%20(The%20996%20Prohibited%20License)-blue.svg">
  </a>

  <a href="https://www.apache.org/licenses/LICENSE-2.0">
    <img alt="code style" src="https://img.shields.io/badge/license-Apache%202-4EB1BA.svg?style=flat-square">
  </a>
</p>

## 修改内容
基于mybatis-plus-3.1.0
1、增加复杂表名实体类映射。比如userinfo->UserInfo。原始的只能生成Userinfo。
2、修改vm模板，修复格式错乱，调整格式。全局生成@TableName。全局生成@TableField。如果没有全局@TableNanme，复杂表名无法处理。
3、添加属性，使其支持自定义数据库关键字。对关键字进行显示转化。

## 使用例子

        //复杂表名，自定义实体类名
        Map<String, String> tableEntityNameMap = new HashMap<>();
        tableEntityNameMap.put("creditor", "creditor");
        tableEntityNameMap.put("repayplan", "RepayPlan");
        tableEntityNameMap.put("scatterinvest", "ScatterInvest");
        tableEntityNameMap.put("transferproject", "TransferProject");
        tableEntityNameMap.put("transferstatus", "TransferStatus");
        tableEntityNameMap.put("undertakeinfo", "UndertakeInfo");
        tableEntityNameMap.put("userinfo", "UserInfo");
        tableEntityNameMap.put("t_user", "User");

        // 策略配置
        StrategyConfig strategy = new StrategyConfig();
        strategy.setTableNameEntityNameMap(tableEntityNameMap);
        strategy.setNaming(NamingStrategy.underline_to_camel);

        strategy.setColumnNaming(NamingStrategy.underline_to_camel);
        strategy.setEntityLombokModel(true);
        strategy.setRestControllerStyle(true);
        strategy.setInclude(("creditor,repayplan,scatterinvest,status,transact,transferproject," +
                "transferstatus,undertakeinfo,userinfo,t_user").split(","));
        strategy.setControllerMappingHyphenStyle(true);
        strategy.setTablePrefix(pc.getModuleName() + "_");
        generator.setStrategy(strategy);
        generator.execute();

## Maven
    
        <dependency>
            <groupId>com.open</groupId>
            <artifactId>mybatis-plus-generator-fix</artifactId>
            <version>3.1.1.1.fix</version>
        </dependency>

        <dependency>
            <groupId>org.apache.velocity</groupId>
            <artifactId>velocity-engine-core</artifactId>
            <version>2.1</version>
        </dependency>

        <repositories>
            <repository>
                <id>maven-repo</id>
                <url>https://raw.githubusercontent.com/fanlushuai/maven-repo/master/</url>
            </repository>
        </repositories>
    
## License

MyBatis-Plus is under the Apache 2.0 license. See the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) file for details.
