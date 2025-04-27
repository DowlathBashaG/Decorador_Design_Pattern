# Decorador_Design_Pattern



Decorader Design Pattern :

		1. Wrapper  [ it add behavior to an existing object with out  affecting the other objects.
		 
		2. Add functionality or behavior

		3. Single Responsibility Principle

		4. Dynamically compute the behavior of the application

		5. It is the combination of inheritance and composition.


DisAdvantage :

		1. New class for every feature.
		
		2. No of. object (more)
		
		3. more complex for the clients.
1. 

 Phone.java (interface) :
 ----------------------

		public interface Phone{
		
		String build();
		
		}
		

2. 

BasicPhone.java :
---------------

		public class BasicPhone implements Phone {
			@Override
			public String build() {
				return "Screen, Battery, Processor";
			}
		}
		

3. 

SmartPhone.java :
---------------

In order to decorader the phone, abstract method is required.


		//Decorator
		public abstract class SmartPhone implements Phone {

			private final Phone phone;

			public SmartPhone(Phone phone) {
				this.phone = phone;
			}

			public String build() {
				return phone.build();
			}
		}


4. 

ApplePhone.java :
---------------

		public class ApplePhone extends SmartPhone {
			public ApplePhone(Phone phone) {
				super(phone);
			}

			@Override
			public String build() {
				return super.build() + addOS();
			}

			private String addOS() {
				return "IOS v1.0";
			}
		}


5.  

AndroidPhone.java :
-----------------

		public class AndroidPhone extends SmartPhone {
			public AndroidPhone(Phone phone) {
				super(phone);
			}

			@Override
			public String build() {
				return super.build() + addOS();
			}

			private String addOS() {
				return "Android OS v6.0";
			}
		}

6.

DecoraderExample.java :
---------------------


		public class DecoratorExample {

			public static void main(String[] args) {


				Phone androidPhone = new AndroidPhone(new BasicPhone());
				System.out.println(androidPhone.build());


				Phone applePhone = new ApplePhone(new BasicPhone());
				System.out.println(applePhone.build());


				Phone nokiaWindowsPhone = new NokiaPhone(new WindowsPhone(new BasicPhone()));
				System.out.println(nokiaWindowsPhone.build());

				Phone nokiaAndroidPhone = new NokiaPhone(new AndroidPhone(new BasicPhone()));
				System.out.println(nokiaAndroidPhone.build());

			}
		}

7.

WindowsPhone.java :
-----------------

		public class WindowsPhone extends SmartPhone {
			public WindowsPhone(Phone phone) {
				super(phone);
			}

			public String build() {
				return super.build() + addOS();
			}

			private String addOS() {
				return " Windows Phone v1.0";
			}

		}
		
8.

NokiaPhone.java
----------------

		public class NokiaPhone extends SmartPhone {
			public NokiaPhone(Phone phone) {
				super(phone);
			}

			public String build() {
				return super.build() + addBranding(); // branding is behavior
			}

			private String addBranding() {
				return " Microsoft Phone";
			}
		}

