---
layout: post
title:  "상속"
date:   2023-05-15 17:00
categories: Java
thumbnail: /assets/img/posts/java.png
Authors : Hwet
comments: 1
---

<h3>상속이란?</h3>
<p>상속은 상위 클래스(부모)의 멤버를 자식 클래스(자식)에게 물려주어 자식 클래스에서 접근 제한(private)을 갖는 
필드와 메서드를 제외한 public, protected, default로 선언되어있는 모든 변수와 메서드를 사용할 수 있게 해준다.</p>
`public : 모든 접근을 허용`<br>
`protected : 같은 패키지(폴더) 내에 있는 객체와 상속관계의 객체들만 허용`<br>
`default : 같은 패키지(폴더) 내에 있는 객체들만 허용 (상속해도 default 접근 제한 필드 및 메서드를 자식이 물려받을 수 없음)`<br>
`private : 현재 객체 내에서만 허용`

<p>부모 클래스가 변경되면 자식 클래스는 자동으로 영향을 주게 되며, 자식 클래스가 변경된다고 해서 부모에게 영향을 주지 않는다.</p>

<h4>상속의 개념</h4>
- 상속이란 기존 클래스(부모)의 변수와 메소드를 물려받아 좀 더 구체적인 클래스(자식)을 구성하는 것을 의미한다.
- 이러한 상속은 캡슐화, 추상화, 다형성과 더불어 객체지향프로그래밍을 구성하는 특징 중 하나이다.
- 클래스 간의 계층적 관계를 구성함으로써 다형성의 문법적 토대를 마련한다.

<h4>상속의 필요성(장점)</h4>
- 부모 클래스의 변수와 메서드, 코드를 재사용 및 재활용 가능하기 코드 중복의 감소로 인해 개발 시간이 단축된다.
- 완성된 코드를 수정(유지 보수)의 시간이 감소한다. -> 부모 클래스 하나의 수정으로 모든 자식 클래스의 수정 효과를 가져오기 때문

<h4>상속의 특성</h4>
- 부모클래스의 접근 제한을 갖는 필드와 메서드를 제외한 선언되어있는 변수와 메서드를 상속받으며, 생성자와 초기화 블록은 상속되지 않는다.
- 자식클래스의 생성자가 호출될 때, 부모클래스의 기본생성자를 호출한다.


<h4>상속의 잘못된 오해</h4>
- "상속은 코드의 재활용을 위한 문법이다"는 <strong style="color:red">잘못된 문장</strong>이다.

<h4>상속 선언</h4>
- 상속을 선언할 때는 자식 클래스 선언시 자식클래스명 뒤에 <strong style="color:#00FFFF">extends</strong> 키워드를 사용하여 상속한다. 

<h4>상속의 생성자와 super 키워드</h4>
<p>코드를 통해서 이해하고자 한다. 부모클래스(Parent), 자식클래스(Child)가 존재한다.</p>
<p>부모클래스와 자식클래스에 기본생성자와 매개변수 하나를 갖는 생성자가 있다.</p>
<p>생성자의 생성 순서는 부모 -> 자식 순으로 생성된다. 좀 더 구체적인 순서는 super키워드에 따라 달라진다.</p>

> Case 1 : super 키워드 사용 X, 객체생성 시 매개변수 입력 X
<p><details>
<summary style="color:#00FF40;">Case 1 설명</summary>

{% highlight java %}
// 부모 클래스 
public class Parent {
	public String nation;
	
	public Parent() {		// 기본생성자
		this("나라"); // 부모 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
		System.out.println("부모 기본생성자");
	}
	
	public Parent(String nation) {
		this.nation = nation;
		System.out.println("부모 매개변수 : " + nation);
	}
}

// 자식 클래스
public class Child extends Parent{
    public String name;

    public Child() {
        this("이름"); // 자식 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
        // nation = "생성";     // 에러 X -> 부모 생성자를 먼저 불러왔기 때문에 부모 클래스의 객체 사용가능 
        System.out.println("자식 기본생성자");
    }

    public Child(String name) {
        this.name = name;
        System.out.println("자식 매개변수 : " + name);
    }

    public static void main(String[] args) {
        Child child = new Child();
        // System.out.println(child.nation);    // "생성"이 출력됨
    }
}
{% endhighlight %}
<blockquote> 출력 결과
<div>
부모 매개변수 : 나라<br>
부모 기본생성자<br>
자식 매개변수 : 이름<br>
자식 기본생성자</div>
</blockquote>

<h5>생성자의 생성완료 순서 </h5>
<p><strong style="color:#00FFFF">부모매개변수 -> 부모기본 -> 자식매개변수 -> 자식기본</strong> 순으로 생성자의 생성이 완료된다. </p>
<h5>흐름도(Debug로 체크)</h5>
<p>Child child = new Child() => (자식) 기본생성자 실행 => (자식) this키워드로 매개변수생성자 실행 => (자식) 매개변수생성자에서 자동생성된(생략되어있는) 부모의 기본생성자 코드 
=> (부모) 기본생성자 실행 => (부모) 기본생성자 this 키워드 => (부모) 매개변수생성자 전체실행(코드종료) => (부모) 기본생성자 출력코드 (코드종료)=> (자식) 매개변수생성자 실행코드(코드종료) 
=> (자식) 기본생성자 출력코드</p>

</details></p>

> Case 2 : super 키워드 사용 X, 객체생성 시 매개변수 입력 O
<p><details>
<summary style="color:#00FF40;">Case 2 설명</summary>

{% highlight java %}
// 부모 클래스 
public class Parent {
	public String nation;
	
	public Parent() {		// 기본생성자
		this("나라"); // 부모 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
		System.out.println("부모 기본생성자");
	}
	
	public Parent(String nation) {
		this.nation = nation;
		System.out.println("부모 매개변수 : " + nation);
	}
}

// 자식 클래스
public class Child extends Parent{
    public String name;

    public Child() {
        this("이름"); // 자식 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
        System.out.println("자식 기본생성자");
    }

    public Child(String name) {
        this.name = name;
        System.out.println("자식 매개변수 : " + name);
    }

    public static void main(String[] args) {
        Child child = new Child("변수");
    }
}
{% endhighlight %}
<blockquote> 출력 결과
<div>
부모 매개변수 : 나라<br>
부모 기본생성자<br>
자식 매개변수 : 변수</div>
</blockquote>

<h5>생성자의 생성완료 순서 </h5>
<p><strong style="color:#00FFFF">부모매개변수 -> 부모기본 -> 자식매개변수</strong> 순으로 생성자의 생성이 완료된다. </p>
<h5>흐름도</h5>
<p>Debug모드로 직접 해보자</p>

</details></p>

> Case 3-1 : super 키워드 사용 O, 객체생성 시 매개변수 입력 X (super에 매개변수)
<p><details>
<summary style="color:#00FF40;">Case 3-1 설명</summary>

{% highlight java %}
// 부모 클래스 
public class Parent {
	public String nation;
	
	public Parent() {		// 기본생성자
		this("나라"); // 부모 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
		System.out.println("부모 기본생성자");
	}
	
	public Parent(String nation) {
		this.nation = nation;
		System.out.println("부모 매개변수 : " + nation);
	}
}

// 자식 클래스
public class Child extends Parent{
    public String name;

    public Child() {
        this("이름"); // 자식 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
        System.out.println("자식 기본생성자");
    }

    public Child(String name) {
        super(name);
        this.name = name;
        System.out.println("자식 매개변수 : " + name);
    }

    public static void main(String[] args) {
        Child child = new Child();
    }
}
{% endhighlight %}
<blockquote> 출력 결과
<div>
부모 매개변수 : 변수<br>
자식 매개변수 : 이름<br>
자식 기본생성자</div>
</blockquote>

<h5>생성자의 생성완료 순서 </h5>
<p><strong style="color:#00FFFF">부모매개변수 -> 자식매개변수 -> 자식기본</strong> 순으로 생성자의 생성이 완료된다. </p>
<h5>흐름도</h5>
<p>Debug모드로 직접 해보자</p>

</details></p>


> Case 3-1 : super 키워드 사용 O, 객체생성 시 매개변수 입력 X (super에 매개변수 X)
<p><details>
<summary style="color:#00FF40;">Case 3-1 설명</summary>

{% highlight java %}
// 부모 클래스
public class Parent {
public String nation;

	public Parent() {		// 기본생성자
		this("나라"); // 부모 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
		System.out.println("부모 기본생성자");
	}
	
	public Parent(String nation) {
		this.nation = nation;
		System.out.println("부모 매개변수 : " + nation);
	}
}

// 자식 클래스
public class Child extends Parent{
public String name;

    public Child() {
        this("이름"); // 자식 생성자중 String 매개변수 하나의 생성자를 불러온다 (존재한다는 가정하에 -> 없으면 에러)
        System.out.println("자식 기본생성자");
    }

    public Child(String name) {
        super();
        this.name = name;
        System.out.println("자식 매개변수 : " + name);
    }

    public static void main(String[] args) {
        Child child = new Child();
    }
}
{% endhighlight %}
<blockquote> 출력 결과
<div>
부모 매개변수 : 나라<br>
부모 기본생성자<br>
자식 매개변수 : 이름<br>
자식 기본생성자</div>
</blockquote>

<h5>생성자의 생성완료 순서 </h5>
<p><strong style="color:#00FFFF">부모매개변수 -> 부모기본 -> 자식매개변수 -> 자식기본</strong> 순으로 생성자의 생성이 완료된다. </p>
<h5>흐름도</h5>
<p>Debug모드로 직접 해보자</p>

</details></p>