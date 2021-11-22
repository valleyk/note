> # spring bean相关

- **初始化**

通过不同的策略创建合适的bean(factory method, constructor autowiring, or simple instantiation.)例如构造器是否需要传入参数


- **属性填充**


为bean设置相关属性及依赖

- **设置Aware接口的相关依赖**


调用Aware接口的set方法,为bean提供感知能力，例如 BeanNameAware,BeanFactoryAware,
ApplicationContextAware等

- **调用前置处理器**


前置处理器在bean初始化之前被调用

- **调用initializingBean方法**

如果bean实现了initializingBean接口，则调用AfterPorpertySet方法

- **调用自定义的init-method**

调用方法方法定义的init-method

- **调用后置处理器**

在方法的属性都填充完成时候，调用后置处理器，可以用于执行自定义逻辑

- **调用Distruction回调**

- **调用disposeBean方法**


注册销毁bean时需要执行的回调

- **调用Destroy-method**

调用destory method

> # Spring 拓展接口

- InstantiationAwareBeanPostProcessor

在实例化bean的前后

- BeanPostProcessor

在初始化bean的前后