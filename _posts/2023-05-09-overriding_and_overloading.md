---
layout: post
title:  "오버로딩과 오버라이딩"
date:   2023-05-09 10:00
categories: Java
tags: 용어 면접 
comments: 1
---
<오버로딩><br>
	오버로딩은 같은 이름의 함수(메소드)를 여러개 정의하고, 매개변수의 타입과 개수를 다르게 하여 
	다양한 호출에 응답할 수 있게 된다. 

{% highlight java %}
class OverloadingExample{
		void cat(){
			System.out.println("매개변수 없음");
    	}
    	void cat(int a){
			// System.out.println("매개변수 하나");
			System.out.printf("현재 %d마리의 고양이가 있습니다.\n", %d);
			// > 동일한 메소드지만 
    	}
    	void cat(String b){
			//System.out.println("매개변수 하나");
			System.out.printf("고양이가 있는 곳은 %s입니다.\n", %s);
    	}
	}
	// => main메소드에서 호출 가정 한다면
	OverloadingExample ole = new OverloadingExample(); // 
	ole.cat(); 		// => 매개변수 없음 출력
	ole.cat(4);		// => 현재 4마리의 고양이가 있습니다. 출력
	ole.cat("동물병원"); // => 고양이가 있는 곳은 동물병원입니다. 출력
{% endhighlight %}

<오버라이딩><br>sfsdf
    	상위 클래스가 가지고 있는 맴버변수가 하위 클래스로 상속되는 것처럼 상위 클래스가 가지고 있는 메소드도 하위 클래스로
    	상속되어 하위 클래스에 사용할 수 있습니다. 또한, 하위클래스에서 메소드를 재정의해서 사용가능하다.
    	(메소드의 이름, 매개변수, 반환형이 모두 동일한 상황에서 상속받은 메소드를 덮어쓴다고 생각하면 된다.)<br>
    	--> 부모클래스(상위클래스)의 메소드는 무시하고, 자식클래스의(하위클래스)의 메소드를 사용하겠다.
    	
{% highlight java %}
class Woman{ //부모클래스
	public String name;
	public int age;
	//info 메서드
	public void info(){
		System.out.println("여자의 이름은 "+name+", 나이는 "+age+"살입니다.");
	}
}
class Job extends Woman{ 		//Woman클래스(부모클래스)를 상속받음 : 
	String job;
	public void info() {	//부모(Woman)클래스에 있는 info()메서드를 재정의
		super.info();
		System.out.println("여자의 직업은 "+job+"입니다.");
	}
}
public class OverTest {
	public static void main(String[] args) {
		//Job 객체 생성
		Job job = new Job();
		//변수 설정
		job.name = "유리";
		job.age = 30;
		job.job = "프로그래머";
		//호출
		job.info();
	}
}
// ===> 여자의 직업은 프로그래머입니다. 출력
{% endhighlight %}
    	
상속, 인터페이스, 추상클래스에 대한 개념을 공부하고 개념을 이해하는것이 좋아보임
    	