---
layout: post
title: Btrace常见例子
tags: btrace java trace
---

{{ page.title }}
==========================

### 业务代码
```
package com.jiuyan.lc.service.impl;
public class LogServiceImpl {
	public void incrementPicView(String picId, int count) {
		
	}
}
```
---
### btrace

判断入参
```
import static com.sun.btrace.BTraceUtils.*;
import com.sun.btrace.annotations.*;

@BTrace
public class AssertPicView {
	@OnMethod(clazz = "com.jiuyan.lc.service.impl.LogServiceImpl", method = "incrementPicView")
	public static void traceExecute(String picId, int count) {
		if (BTraceUtils.matches("10000", picId)) {
			println(str(count));
		}
	}
}
```

QPS
```
import static com.sun.btrace.BTraceUtils.*;
import com.sun.btrace.annotations.*;

@BTrace
public class CheckPicView {
	private static volatile long methodHit;

	@OnMethod(clazz = "com.jiuyan.lc.service.impl.LogServiceImpl", method = "incrementPicView")
	public static void hitMethod() {
		methodHit++;
	}


	@OnTimer(1000)
	public static void print() {
		println(Strings.strcat("methodHit = ", str(methodHit)));
		methodHit = 0;
	}
}
```

响应时间
```
import static com.sun.btrace.BTraceUtils.*;
import com.sun.btrace.annotations.*;

@BTrace
public class GetLantency {

	@TLS
	// 注意TLS,在一个线程里计算lantency
	private static long startTime = 0;

	@OnMethod(clazz = "com.jiuyan.lc.service.impl.LogServiceImpl", method = "incrementPicView")
	public static void startExecute() {
		startTime = timeNanos();
	}

	//下面两种方法都可以计算lantency
	@OnMethod(clazz = "com.jiuyan.lc.service.impl.LogServiceImpl", method = "incrementPicView", location = @Location(Kind.RETURN))
	public static void endExecute(@Duration long duration) {
		long time = timeNanos() - startTime;
		println(strcat("execute time(nanos): ", str(time)));
		println(strcat("duration(nanos): ", str(duration)));
	}
}
```

---
pom.xml
```
		<dependency>
			<groupId>com.sun.tools.btrace</groupId>
			<artifactId>btrace-client</artifactId>
			<version>1.2.3</version>
		</dependency>
```
参考
https://kenai.com/projects/btrace/pages/UserGuide
