## 工厂方法
'''
//:  interfaces/Factories.java
package interfaces;

class Print{
	public static void print(Object o) {
		System.out.println(o);
	}
}

interface Service{
	void method1();
	void method2();
}

interface ServiceFactory{     
	Service getService();
}

class Implementation1 implements Service{
	Implementation1(){}   //  Package access
	public void method1() {Print.print("Implementation1::method1()");}
	public void method2() {Print.print("Implementation1::method2()");}
}

class Implementation2 implements Service{
	Implementation2(){}   //  Package access
	public void method1() {Print.print("Implementation2::method1()");}
	public void method2() {Print.print("Implementation2::method2()");}
}

class Implementation1Factory implements ServiceFactory{
	Implementation1Factory(){}  //  Package access
	public Service getService() {
		return new Implementation1();
	}
}

class Implementation2Factory implements ServiceFactory{
	Implementation2Factory(){}  //  Package access
	public Service getService() {
		return new Implementation2();
	}
}

public class Factories {
	public static void serviceConsumer(ServiceFactory fact) {
		Service s = fact.getService();
		s.method1();
		s.method2();
	}
	public static void main(String[] args) {
		Print.print("implementation1");
		serviceConsumer(new Implementation1Factory());
		Print.print("implementation2");
		serviceConsumer(new Implementation2Factory());
	}
}
'''
由上述代码可知工厂方法将Service和Service实例化分离。为什么添加额外级别地间隔性呢？一个常见的原因是把类的实例化推迟到子类，让子类决定要实例化的类；另一个原因是想要创建框架。

## 推迟实例化

## 创建框架

