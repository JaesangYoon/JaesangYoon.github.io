---
layout: single
title:  "캡슐화 예제"
---

### 캡슐화

 iv의 접근제어자를 private으로 하면서 외부에서 iv에 대한 직접 접근을 막고 메서드(getter, setter - 모두 접근제어자 public)를 통한 간접 조건만을 허용하는 것. 데이터(iv)를 보호하기 위함.

```java
package ch7;


import java.util.Objects;

class Time {
    private int hour; // 0~23
    private int minute; // 0~59
    private int second; // 0~59

    public Time(int hour, int minute, int second) {
        this.hour = hour;
        this.minute = minute;
        this.second = second;

        System.out.println(hour + "시 " + minute + "분 " + second + "초 입니다");
    }

    public Time() {};



    @Override
    public String toString() {
        return "Time{" +
                "hour=" + hour +
                ", minute=" + minute +
                ", second=" + second +
                '}';
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Time time = (Time) o;
        return hour == time.hour && minute == time.minute && second == time.second;
    }

    @Override
    public int hashCode() {
        return Objects.hash(hour, minute, second);
    }

    public int getHour() {
        return hour;
    }

    public void setHour(int hour) { // 0~23
        if (hour > 24 || hour < 0) { // 범위에 맞지 않을 경우 return.
            System.out.println("Hour의 범위에 맞게 다시 입력해주세요");
            return;
        }
        this.hour = hour;
    }

    public int getMinute() {
        return minute;
    }

    public void setMinute(int minute) { // 0~59
        if (minute > 59 || minute < 0) {
            System.out.println("Minute의 범위에 맞게 다시 입력해주세요");
            return;
        }
        this.minute = minute;
    }

    public int getSecond() {
        return second;
    }

    public void setSecond(int second) { // 0~59
        if (second > 59 || second < 0) {
            System.out.println("Second 범위에 맞게 다시 입력해주세요");
            return;
        }
        this.second = second;
    }
}


public class EncapsulationTimeTest {
    public static void main(String[] args) {
        Time time = new Time();
        time.setHour(37); // 범위를 넘어선다
        time.setMinute(90); // 범위를 넘어선다
        time.setSecond(19);

        System.out.println("time = " + time);



    }
}
```
