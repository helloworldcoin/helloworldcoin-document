### 代码规范
#### 1.贫血模型
规定采用贫血模型进行开发，若对象有行为，则将该行为写在该对象伴随的工具类中，伴随的工具类的类名要求是该类的名字+Tool后缀。
案例：[区块对象模型](https://github.com/helloworldcoin/helloworldcoin-java/blob/master/helloworldcoin-core/src/main/java/com/helloworldcoin/core/model/Block.java)
[区块对象模型的伴随工具类](https://github.com/helloworldcoin/helloworldcoin-java/blob/master/helloworldcoin-core/src/main/java/com/helloworldcoin/core/tool/BlockTool.java)

#### 2.工具类取名规范
与业务无关的工具类，类名以Util后缀结尾。  
与业务相关的工具类，类名以Tool后缀结尾。

#### 3.DTO VO MODEL PO命名
PO命名规范：类名以Po后缀结尾，对象名以Po后缀结尾，对象数组、列表后缀加s。  
DTO命名规范：类名以Dto后缀结尾，对象名后缀不要加Dto，对象数组、列表后缀加s。 
注意：只有两台节点间通信才会用到DTO，为了清晰，创建了子模块helloworldcoin-netcore-dto专门存放所有的DTO。 
MODEL命名规范：类名不需要以特别后缀标识结尾，对象数组、列表后缀加s。  
VO命名规范：类名以Vo后缀结尾，对象名后缀不要加Vo，对象数组、列表后缀加s。  

#### 4.不要自己造轮子
案例：Base58工具类  
项目需要一个base58编码与解码的工具，这种轮子直接到开源项目中寻找就可以了，开源项目中的轮子都是经过考验的，比自己写的强太多。

#### 5.少用高级语言的特性
少用、不用高级语言的特性，原因是特性的移植性差，例如go语言就没有重载、泛型等。高级特性包括：重载、泛型、继承、可变参数、包装等。

#### 6.构造器
构造器内的代码清单应足够简单，不做任何逻辑。

#### 7.隔离
Helloworldcoin项目由8个子模块组成。原则上，只有子模块helloworldcoin-crypto、子模块helloworldcoin-util可以引入外部项目。其它子模块(其余6个子模块)有引入外部项目的需求时，通过这两个项目间接使用。这两个子模块隔离了内部项目(其余6个子模块)和外部项目的直接交互，对内部项目(其余6个子模块)屏蔽了实现细节，可以随时切换外部项目的实现。

#### 8.接口约定
接口一律采用JSON数据格式；接口不允许返回空字符串、null结果；接口入参出参不允许使用包装类型。
