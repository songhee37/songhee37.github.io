---
layout: post
title: JAVA (junit , @AfterEach)
---
<hr>
<pre>
<code>
1. @AfterEach

@Test 코드 작성 시,    
    // Test가 끝날때마다 레파지토리를 꺠끗하게 만들어주는 코드를 만들어줘야한다.
    // 메소드의 순서는 임의로 지정하는게 아니여서, 여러개의 @Test  시 에러가 날수도 있다.
    @AfterEach
    public void afterEach() {
        repository.clearStore();
    }
</code>
</pre>
<hr>

2. 회원가입 시, 
optional<t>인 경우, ifpresent 로 중복체크 가능.

<pre>
<code>
    // 회원가입
    public Long join(Member member){

        // 같은 이름이 있는 중복 회원 x
        validateDuplicateMember(member);//증복회원검증.
        memberRepository.Save(member);
        return member.getId();
    }

    private void validateDuplicateMember(Member member) {
        memberRepository.findByName(member.getName())
                .ifPresent(m -> {
            throw new IllegalStateException("이미 존재하는 회원입니다.");
        });
    }
</code>
</pre>
