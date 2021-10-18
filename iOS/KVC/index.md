`setValue` 机制

+ 程序优先调用 `set:`属性值方法，代码通过 `setter` 方法完成设置。注意，这里的是指成员变量名，首字母大小写要符合 `KVC` 的命名规则，下同

+ 如果没有找到 `setName：`方法，`KVC` 机制会检查 `+ (BOOL)accessInstanceVariablesDirectly`方法有没有返回`YES`，默认该方法会返回 `YES`，如果你重写了该方法让其返回 `NO` 的话，那么在这一步 `KVC` 会执行 `setValue：forUndefinedKey：` 方法，不过一般开发者不会这么做。所以 `KVC` 机制会搜索该类里面有没有名为 `_` 的成员变量，无论该变量是在类接口处定义，还是在类实现处定义，也无论用了什么样的访问修饰符，只在存在以_命名的变量，`KVC` 都可以对该成员变量赋值。

+ 如果该类即没有 `set：`方法，也没有_成员变量，`KVC` 机制会搜索 `_is` 的成员变量。

+ 和上面一样，如果该类即没有`set：`方法，也没有 `_` 和 `_is` 成员变量，`KVC` 机制再会继续搜索和 `is` 的成员变量。再给它们赋值。

+ 如果上面列出的方法或者成员变量都不存在，系统将会执行该对象的 `setValue：forUndefinedKey：`方法，默认是抛出异常。



`valueForKey` 机制 

+ 首先按 `get`, `is` 的顺序方法查找 `getter` 方法，找到的话会直接调用。如果是 `BOOL` 或者 `Int` 等值类型， 会将其包装成一个`NSNumber` 对象。

+ 如果上面的 `getter` 没有找到，`KVC` 则会查找 `countOf`，`objectInAtIndex` 或 `AtIndexes` 格式的方法。如果 `countOf` 方法和另外两个方法中的一个被找到，那么就会返回一个可以响应 `NSArray` 所有方法的代理集合(它是 `NSKeyValueArray`，是 `NSArray`的子类)，调用这个代理集合的方法，或者说给这个代理集合发送属于 `NSArray` 的方法，就会以 `countOf`，`objectInAtIndex`或`AtIndexes` 这几个方法组合的形式调用。还有一个可选的 `get:range:` 方法。所以你想重新定义 `KVC` 的一些功能，你可以添加这些方法，需要注意的是你的方法名要符合 `KVC` 的标准命名方法，包括方法签名。

+ 如果上面的方法没有找到，那么会同时查找 `countOf`，`enumeratorOf`，`memberOf` 格式的方法。如果这三个方法都找到，那么就返回一个可以响应 `NSSet` 所的方法的代理集合，和上面一样，给这个代理集合发 `NSSet` 的消息，就会以 `countOf`，`enumeratorOf`，`memberOf` 组合的形式调用。

+ 如果还没有找到，再检查类方法 `+ (BOOL)accessInstanceVariablesDirectly`，如果返回 `YES` (默认行为)，那么和先前的设值一样，会按 `_`,`_is`,`is` 的顺序搜索成员变量名，这里不推荐这么做，因为这样直接访问实例变量破坏了封装性，使代码更脆弱。如果重写了类方法 `+ (BOOL)accessInstanceVariablesDirectly` 返回 `NO` 的话，那么会直接调用 `valueForUndefinedKey:`方法，默认是抛出异常。


