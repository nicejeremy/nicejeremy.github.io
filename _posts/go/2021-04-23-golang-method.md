---
layout: post
title:  "[Golang] Method와 Interface"
date:   2021-04-23
categories: golang
tags: golang
---

* content
{:toc}

# 메서드 (Method)
Go 언어에는 클래스의 개념이 없다. 하지만 Type에 메서드를 정의할 수 있는데 메서드는 특수한 수신자(Receiver) 인자를 받는 함수이다. 이때 리시비(Receiver)는 `func 키워드와 함수명 사이`에 정의한다.

{% highlight go %}
type Triangle struct{ width, height float64 }

func (triangle Triangle) Area() float64 {
    return triangle.width * triangle.height / 2
}

func TestTriangle(t *testing.T) {
    triangle := Triangle{2, 3}
    assert.Equal(t, float64(3), triangle.Area())
}
{% endhighlight %}

# 인터페이스 (Interface)
인터페이스는 메서드들의 묶음(집합)이다. OOP의 다른 언어에서 인터페이스를 구현할 때 implement 키워드를 이용해 어떤 인터페이스를 구현하는지 선언하는것과는 달리 Go에서는 명시적으로 어떤 인터페이스를 구현하는지 명시하지 않는다. 인터페이스에서 정의한 메서드들을 모두 구현했다면 해당 인터페이스를 구현한것이 된다.

{% highlight go %}

type Car interface {
    drive()
    park()
}

type Truck struct {
    Gear  Gear
    Power Power
    ...
}

func (truck Truck) drive() {
    truck.Power.on()
    truck.Gear.drive()
}

func (truck Truck) park() {
    truck.Gear.parking()
    truck.Power.off()
}

{% endhighlight %}


# References
- [Methods](https://tour.golang.org/methods/1)
