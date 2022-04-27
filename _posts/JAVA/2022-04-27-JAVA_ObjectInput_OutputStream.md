---
layout: post
title:  "[JAVA] ObjectInputStream, ObjectOutputStream 정리"
categories: tech
tags: java
comments: true
---
**Contents**

<br/>
<br/>

---
# ObjectOutputStream
객체를 출력하는 스트림이다.

객체를 생성할 때 생성자의 매개변수로 `FileOutputStream` 객체를 넣어야 한다.
```
ex) ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(File));
```
<br/>

`writeObject(객체)` : 객체 단위로 출력한다.

- 직렬화(Serializable)가 되지 않은 객체는 출력이 불가능하다. 그러므로 `implements Serializable`를 통해 구현을 꼭 하자.
- Serializable를 구현하지 않았을 경우 `java.io.NotSerializableException` 예외를 처리해야 한다.

<br/>

즉 직렬화가 구현되어 있는 자료형은 바로 출력이 가능하다.

ArrayList는 직렬화가 구현된 클래스라서 아래와 같이 한번에 출력이 가능하다.

```java
ArrayList implements Serializable {}

...
ArrayList<Info> al = new ArrayList<>();

ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(File));
oos.writeObject(al);
```

이 경우에는 **Info 클래스 또한 직렬화를 구현**한 상태여야 한다.

<br/>
<br/>

# ObjectInputStream
객체를 읽어오는 스트림이다.

객체를 생성할 때 생성자의 매개변수로 FileInputStream객체를 넣어야 한다.
```
ex) ObjectInputStream ois = new ObjectInputStream(new FileOutputStream(File));
```
<br/>

`readObject()` : Object 변수로 값을 받으면 된다.

- Object형 변수로 해당 값을 받은 후(자동 업캐스팅) 원하는 자료형으로 다운캐스팅을 해서 사용하면 된다.
```java
Object obj = ois.readObject();
Info i = (Info) obj;
```

`readObject()`를 사용할 때 파일에 입력된 Object가 없어서 읽어온 변수가 없을 때 **EOFException** 예외가 발생한다.

try / catch를 통하여 예외처리를 하면 된다.

