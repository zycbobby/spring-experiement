

# Purpose

This project to test the order of running static block and spring bean initialization

Experiement: can static block access autowired object?

**先要明白Static块是什么时候运行的**

Static块是在类第一次被加载的时候运行

**spring的对象初始化是在什么时候运行的**
> Assuming the bean is a singleton, and isn't configured for lazy initialisation, then it's created when the context is started up. getBean() just fishes it out.
Lazy-init beans will only be initialised when first referenced, but this is not the default. Scoped beans (e.g. prototype-scoped) will also only be created when first referenced.



**回过头来想这个问题**

The static initializer is executed by the classloader as part of loading the class before any code is granted access to the class. Since Spring must instantiate the class--which definitely requires loading the class--before it can call setters on that instance, the static initializer block has already run.




