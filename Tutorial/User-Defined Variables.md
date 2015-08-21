## 用户定义变量

数据库支持用户自定义变量，自定义变量使用`@`开头，能够被用于任何表达式和参数中。变量是不能持久的，作为范围为 session，这就意味着变量只在定义它的那个 session 里是有效的。一个变量通常使用 SET命 令来声明：

	SET @USER = 'Joe';

变量也可以通过使用 SET() 方法来改变值。在查询中可以直接使用：

	SET @TOTAL = NULL;
	SELECT X, SET(@TOTAL, IFNULL(@TOTAL, 1.) * X) F FROM SYSTEM_RANGE(1, 50);

变量不能被设置为 NULL 值，变量的类型是变量自动分配的，也就是说，在变量使用前变量的定义并不是必须（也不是必需）的，在声明变量时没有限制，大对象（LOB）也被支持。