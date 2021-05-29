### Функциональность валидации номеров банковских карт.

### Материалы для тестирования

[Номера карт](https://docs.google.com/document/d/1Szm33_53LqAecQUNGqLYmjHRV3NudmnHytCcYYtu3EM/edit?usp=sharing)

[Домашнее задание](https://github.com/netology-code/javaqa-homeworks/tree/master/intro)

### Шаги для воспроизведения

- Открыть программу IDEA
- Завести новый проект
- Дать проекту название "Main"
- Создать ClassMain
- Скопирповать переменную и вставить в IDEA
- Поменять номер карты в 4-ой строке на номер из списка
- Запустить метод Ctrl+Shift+F10

### Переменная

<pre><code> public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
} </code></pre>


### Результат

Ожидаемый:
Все номера из списка валидные

Фактический:
Не все номера из списка валидные 

### Cкриншот ошибки
![Visa](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/4716476782716823070.png)
![American Express (AMEX)](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/347219254707506.png)
![](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/342969472785685.png)![](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/374457377017470.png)
![Discover](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/6011514970957871704.png)
![JCB](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/3542721464542799048.png)
![Diners Club - Carte Blanche](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/30262275369270.png)![](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/30283469346106.png)![](https://github.com/MashaOsipova/Java1.1/blob/1d6b362368375082fad692e6b016a73039a3ea45/30453905757451.png)

### Окружение

Windows 10
Java version "11.0.9.1"
IntelliJ IDEA Community Edition 2020.3.1
