## Bean
Spring => POJO(plain, old java object) = ‘Beans’
Beans는 애플리케이션의 핵심을 이루는 객체이며, 
Spring IoC(Inversion of Control) 컨테이너에 의해 인스턴스화, 관리, 생성

### Spring Container의 Bean 관리
– Bean 객체의 생성 -> 의존 객체 주입(DI) -> 초기화 -> 이용 -> 삭제
등 객체의 life-cycle에 관련된 작업을 수행함 
– 각 bean에 대해 callback method들을 호출

<img width="626" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/95747179-a11c-416b-a849-9df948d04b2b">

### Bean의 scope 설정
– Bean 객체(instance)를 언제 어떻게 생성할지를 지정
– Spring container는 기본적으로 각 bean 설정에 대해 하나의 bean
instance만 생성해서 공유 (-> singleton)
– Scope 설정을 통해 변경 가능 (@Scope annotation 사용)
<img width="395" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/61b29cc7-2799-41ed-845c-ae96fb6f8a2a">

singleton 
Piano piano1 = (Piano)applicationContext.getBean(“piano”);
Piano piano2 = (Piano)applicationContext.getBean(“piano”);
System.out.println(piano1 == piano2); // “true”

prototype
Piano piano1 = (Piano)applicationContext.getBean(“piano”);
Piano piano2 = (Piano)applicationContext.getBean(“piano”);
System.out.println(piano1 == piano2); // “false




