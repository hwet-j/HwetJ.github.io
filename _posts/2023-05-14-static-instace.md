---
layout: post
title:  "Static과 Instace 차이"
date:   2023-05-15 11:00
categories: Java
thumbnail: /assets/img/posts/java.png
Authors : Hwet
tags: Static Instace
comments: 1
---

<h3>Static과 Instace</h3>
<h5>static</h5>
<p>사전적 의미로 정적인, 고정 이라는 의미를 가지고 있다.</p>
<p><strong>static으로 선언된 멤버에는 객체를 생성하지 않고도 static 자원에 접근이 가능</strong>하다.</p>
<p>static으로 정적 멤버를 선언하게 되면 프로그램을 실행될 때 메모리에 할당되며, 프로그램이 종료될 떄 해제된다.</p> 

-------------------

<h5>인스턴스</h5>
<p>인스턴스 멤버는 객체(인스턴스)를 생성한 뒤 사용할 수 있는 필드 또는 메서드이다.</p>
<p><strong>인스턴스 멤버는 객체에 소속된 멤버이기 때문에 객체 없이는 사용할 수 없다. <strong></strong></p>
<p>피자라는 클래스는 도우, 토핑, 소스, 재료 등 피자를 만드는데 필요한 여러가지 구성요소(멤버변수)를 가지고 있다.
여기서 만들어지는 결과물(Object)은 피자라는 객체가 되며, 만들어지는 방식에 따라 여러가지 피자(Instance)가 생성될 수 있으며
이러한 피자가 만들어지는 과정, 즉 피자를 굽는다는 행위가 '인스턴스화 하다'라고 보면 된다.</p>
<p></p>1) 피자(클래스)라는 틀에서 -> 2) 피자를 만든다(인스턴스화) -> 3) 이에 결과물로 피자(인스턴스)가 생성된다</p>
<p>피자를 굽는 과정에 따라 여러가지 다른 피자들이 만들어 지는데 이 피자들을 인스턴스라고 말한다.</p>

-------------------------

```java
public class Test {
    // 필드 
    String f1 = "instance";			// static이 붙지 않으면 instace 필드 
    static String f2 = "class, static...";

    // 메서드
    void m1() {
        this.f1 = "m1() 메서드에서 접근";
        this.f2 = "m1()메서드에서 접근";
    }

    static void m2() {
        // this.f1 = "m2() 메서드에서 접근";		// 에러 발생 (Cannot use this in a static context)
        // this.f2 = "m2()메서드에서 접근";
        // f1 = "m2() 메서드에서 접근";		// 에러 발생 (Cannot make a static reference to the non-static field)
        f2 = "m2() 메서드에서 접근";
        System.out.println("m2() 메서드 호출");
    }

    public static void main(String[] args) {
        System.out.println(f2); // class, static...
        m2(); // m2() 메서드 호출;
        // ==> 객체 생성없이 static 멤버에 접근
        
        // 인스턴스 멤버는 객체 생성없이는 접근이 불가능하다.
        //m1();  // --> 에러
        Test te = new Test();
        te.m1();        // --> 객체를 통해 호출 가능
    }

}
```

<p>Test라는 클래스에는 f1과 f2라는 객체와 m1, m2 메서드가 있다. f2 와 m2는 static 선언하였다. </p>
<p>앞서 말한듯이 static으로 선언하게 되면 메모리에 할당되어야 하는데 m2()메서드에 this라는 함수를 통해 객체를 호출 하게되면 오류가 나오는 이유는 
static은 클래스의 소속인데 클래스가 인스턴스 변수에 접근 하려면 어떤 인스턴스의 변수인지 알아야하는데 알 수 없기 때문이다.</p>
<p>간단하게 이해하면 static으로 선언된 멤버가 메모리에 저장될 때 this라는 키워드로 받을 수 있는 object가 존재하지 않기 떄문이다. </p>

----------------------------

<h3>클래스 변수와 인스턴스 변수</h3>
##### 인스턴스 변수(instance variable)
<p>클래스 영역에 선언되며, 클래스의 인스턴스를 생성할 때 만들어집니다. 그렇기 때문에 인스턴스 변수의 값을 읽어오거나 저장하기 위해서는 먼저 인스턴스의 생성이 필요하다.</p>
<p><strong>인스턴스는 독립적인 저장공간을 가지므로 서로 다른 값을 가질 수 있다.</strong> 인스턴스마다 고유한 상태를 유지해야하는 속성의 경우 , 인스턴스 변수로 선언한다.</p>

##### 클래스 변수(class variable)
<p>클래스(static,정적) 변수를 선언하는 방법은 인스턴스 변수 앞에 제어자 static을 붙여주면 된다.
<strong>인스턴스 변수와 달리 클래스 변수는 공통된 저장공간(변수)를 공유</strong>하게 됩니다. 
한 클래스의 모든 인스턴스들이 공통적인 값을 유지해야하는 속성의 경우, 클래스 변수로 선언한다.</p>
<p>또한, 인스턴스 변수와 다르게 객체 생성없이 언제든지 사용가능하다.</p>

##### 지역 변수(local variable)
<p>메서드 내에서 선언되어 선언된 메서드 내에서만 사용가능하며, 메서드가 종료되면 소멸된다. for, while문과 같은 블럭 내에서 선언된 변수는 일반적으로 지역변수 이며 <strong>블럭{}을 벗어나면 소멸되어 사용불가하다.</strong></p>

-------------------------
### 클래스 멤버와 인스턴스 멤버간의 참조와 호출
<p>같은 클래스에 속한 멤버들 간에는 별도의 인스턴스를 생성하지 않고도 서로 참조 또는 호출이 가능하다. 단, 클래스 멤버가 인스턴스 멤버를 참조 또는 호출하고자 하는 경우네는 인스턴스를 생성해야한다.</p>
<p>인스턴스 멤버가 존재하는 시점에 클래스 멤버는 항상 존재하지만, 클래스 멤버가 존재하는 시점에서는 인스턴스 멤버가 존재하지 않을 수 있기 때문이다. <br>
같은 이유로 클래스 멤버에서 this함수를 사용한 호출은 불가능하다.(this가 참조할 object가 존재하지 않기 떄문)</p>

[


---------------------](https://hwet-j.github.io/#/)


[참고][https://bambookim.tistory.com/17](https://bambookim.tistory.com/17) <br>
[참고][https://gangnam-americano.tistory.com/20](https://gangnam-americano.tistory.com/20)  <br>
[참고][https://dkswnkk.tistory.com/444](https://dkswnkk.tistory.com/444) 