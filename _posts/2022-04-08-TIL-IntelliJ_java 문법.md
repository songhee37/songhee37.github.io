---
layout: post
title: Intellj mac 단축키 모음
---
<hr>
1. Optional 클래스

java.util.Optional<T> 클래스
Optional<T> 클래스는 Integer나 Double 클래스처럼 'T'타입의 객체를 포장해 주는 래퍼 클래스(Wrapper class)입니다.

따라서 Optional 인스턴스는 모든 타입의 참조 변수를 저장할 수 있습니다. 

 *** 복잡한 조건문 없이도 널(null) 값으로 인해 발생하는 예외를 처리할 수 있게 됩니다.

만약 참조 변수의 값이 만에 하나 null이 될 가능성이 있다면, ofNullable() 메소드를 사용하여 Optional 객체를 생성하는 것이 좋습니다.

ofNullable() 메소드는 명시된 값이 null이 아니면 명시된 값을 가지는 Optional 객체를 반환하며, 명시된 값이 null이면 비어있는 Optional 객체를 반환합니다.

> 실습예제
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");

System.out.println(opt.get()); >> 결과는 ? 자바 Optional 객체

<hr>
2. Junit Assertions

import org.junit.jupiter.api.Assertions;
import static org.assertj.core.api.Assertions.*;

위에 두개를 사용했다.

<pre>
<code>
 @Test
    public void save() {
        Member member = new Member();
        member.setName("spring");
        repository.Save(member);
        Member result = repository.findById(member.getId()).get();
        Assertions.assertEquals(member,result);
        assertThat(member).isEqualTo(result); // result 대신에 null로 되면 test에서 튕겨냄.
        //System.out.println("result = "+(result == member));
    }
</code>
</pre>
